<template>
  <div id="app">
    <div class="header">
      <img src="@/assets/logo.png" class="logo" />
    </div>
    <div class="content">
      <h1>Athletic Participation</h1>
      <component ref="comp" :is="currentStep" />
      <button v-if="currentIndex < 6" @click="nextStep">Next Step</button>
      <p class="error" v-if="error">{{ error }}</p>
    </div>
    <div class="footer">Covenant Christian High School Athletic Department</div>
  </div>
</template>

<script>
import firebase from 'firebase/app'
import 'firebase/firestore'
import Step0 from '@/components/Step0'
import Step1 from '@/components/Step1'
import Step2 from '@/components/Step2'
import Step3 from '@/components/Step3'
import Step4 from '@/components/Step4'
import Step5 from '@/components/Step5'
import Step6 from '@/components/Step6'

const app = firebase.initializeApp({
  apiKey: 'AIzaSyCg_FVHdzP3kvRAyrnpE2bJUsQfMRUgFW4',
  authDomain: 'my-covenant.firebaseapp.com',
  databaseURL: 'https://my-covenant.firebaseio.com',
  projectId: 'my-covenant',
  storageBucket: 'my-covenant.appspot.com',
  messagingSenderId: '945207168321',
  appId: '1:945207168321:web:e42d0845df84c8c24e65c0',
})
const store = app.firestore()

export default {
  name: 'App',
  components: {
    Step0,
    Step1,
    Step2,
    Step3,
    Step4,
    Step5,
    Step6,
  },
  data: () => {
    return {
      currentIndex: 0,
      currentStep: 'Step0',
      docID: null,
      error: '',
    }
  },
  methods: {
    advanceStep() {
      this.currentIndex++
      this.currentStep = 'Step' + this.currentIndex
    },
    nextStep() {
      this.error = ''
      switch (this.currentIndex) {
        case 0:
          this.saveStep0()
          break
        case 1:
          this.saveStep1()
          break
        case 2:
          this.saveStep2()
          break
        case 3:
          this.saveStep3()
          break
        case 4:
          this.saveStep4()
          break
        case 5:
          this.saveStep5()
          break
      }
    },
    saveStep0() {
      const student = this.$refs.comp.$refs.studentName.value.trim()
      const parent = this.$refs.comp.$refs.parentName.value.trim()
      if (student === '' || parent === '') {
        this.error = 'You must enter both student and parent names to continue.'
      } else {
        store
          .collection('athletic_participation')
          .add({
            started: firebase.firestore.Timestamp.fromDate(new Date()),
            student,
            parent,
            year: '2020-2021',
          })
          .then((result) => {
            if (result.id) {
              this.docID = result.id
              this.advanceStep()
            } else {
              this.error =
                'There was an error in processing your request. Please try again later.'
            }
          })
          .catch(() => {
            this.error =
              'There was an error in processing your request. Please try again later.'
          })
      }
    },
    saveStep1() {
      const forms = this.$refs.comp.$data.parent
      if (forms === false) {
        this.error =
          'You must acknowledge that you have completed the required enrollment forms before continuing.'
      } else {
        store
          .doc(`athletic_participation/${this.docID}`)
          .set(
            {
              enrollment_forms: true,
            },
            { merge: true }
          )
          .then(() => {
            this.advanceStep()
          })
          .catch(() => {
            this.error =
              'There was an error in processing your request. Please try again later.'
          })
      }
    },
    saveStep2() {
      const p1 = this.$refs.comp.$data.page1
      const p2 = this.$refs.comp.$data.page2
      const p3 = this.$refs.comp.$data.page3
      const p4 = this.$refs.comp.$data.page4
      const p5 = this.$refs.comp.$data.page5
      store
        .doc(`athletic_participation/${this.docID}`)
        .set(
          {
            p1,
            p2,
            p3,
            p4,
            p5,
          },
          { merge: true }
        )
        .then(() => {
          this.advanceStep()
        })
        .catch(() => {
          this.error =
            'There was an error in processing your request. Please try again later.'
        })
    },
    saveStep3() {
      const exception = this.$refs.comp.$data.exception
      const parent1 = this.$refs.comp.$data.parent1
      const parent2 = this.$refs.comp.$data.parent2
      const student = this.$refs.comp.$data.student
      if (parent1 === false || parent2 === false || student === false) {
        this.error = 'You must acknowledge each item before continuing.'
      } else {
        store
          .doc(`athletic_participation/${this.docID}`)
          .set(
            {
              handbook_exception: exception,
              handbook_parent1: parent1,
              handbook_parent2: parent2,
              handbook_student: student,
            },
            { merge: true }
          )
          .then(() => {
            this.advanceStep()
          })
          .catch(() => {
            this.error =
              'There was an error in processing your request. Please try again later.'
          })
      }
    },
    saveStep4() {
      const student = this.$refs.comp.$data.student
      const parent = this.$refs.comp.$data.parent
      if (student === false || parent === false) {
        this.error = 'You must acknowledge each item before continuing.'
      } else {
        store
          .doc(`athletic_participation/${this.docID}`)
          .set(
            {
              concussion_sca_student: student,
              concussion_sca_parent: parent,
            },
            { merge: true }
          )
          .then(() => {
            this.advanceStep()
          })
          .catch(() => {
            this.error =
              'There was an error in processing your request. Please try again later.'
          })
      }
    },
    saveStep5() {
      const parent = this.$refs.comp.$data.parent
      if (parent === false) {
        this.error = 'You must acknowledge before continuing.'
      } else {
        store
          .doc(`athletic_participation/${this.docID}`)
          .set(
            {
              finished: firebase.firestore.Timestamp.fromDate(new Date()),
              transportation: parent,
            },
            { merge: true }
          )
          .then(() => {
            this.advanceStep()
          })
          .catch(() => {
            this.error =
              'There was an error in processing your request. Please try again later.'
          })
      }
    },
  },
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Work+Sans:wght@400;700&display=swap');

html,
body {
  background: #4a6830;
  font-family: 'Work Sans';
  margin: 0;
  padding: 0;
}

button {
  background: #4e9db6;
  border: none;
  border-radius: 1vw;
  color: white;
  font-family: 'Work Sans';
  font-size: 1.25em;
  padding: 1vw;
}

input {
  font-family: 'Work Sans';
  font-size: 1em;
}

.acknowledged {
  background: #4a6830;
  color: white;
  display: inline-block;
  padding: 1vw;
  text-transform: uppercase;
}
.content {
  background: white;
  padding: 2vw;
}
.error {
  color: red;
  font-weight: bold;
}
.footer {
  color: white;
  min-height: 5vh;
  padding: 1vw;
}
.header {
  padding: 1vw;
}
.logo {
  max-width: 90vw;
}
</style>
