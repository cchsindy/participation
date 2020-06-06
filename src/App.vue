<template>
  <div id="app">
    <h1>Athletic Participation</h1>
    <component ref="comp" :is="currentStep" @saveStep="saveStep" />
    <button v-if="currentIndex < 6" @click="nextStep">Next Step</button>
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
// eslint-disable-next-line no-unused-vars
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
    }
  },
  methods: {
    advanceStep() {
      this.currentIndex++
      this.currentStep = 'Step' + this.currentIndex
    },
    nextStep() {
      if (this.currentIndex === 0) {
        const student = this.$refs.comp.$refs.studentName.value.trim()
        const parent = this.$refs.comp.$refs.parentName.value.trim()
        store
          .collection('athletic_participation')
          .add({
            started: firebase.firestore.Timestamp.fromDate(new Date()),
            student,
            parent,
          })
          .then((result) => {
            if (result.id) {
              this.docID = result.id
              this.advanceStep()
            }
          })
      }
    },
    saveStep(data) {
      console.log(data)
    },
  },
}
</script>

<style>
#app {
  /* font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; */
}
</style>
