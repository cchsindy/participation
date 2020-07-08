<template>
  <div>
    <h2>Step 1</h2>
    <h3>Required Enrollment Forms</h3>
    <p>
      I have completed the Student Emergency Contacts, Student Medical
      Information, and Non-prescription Medication Permission forms in
      MySchoolApp.
    </p>
    <button @click="sign" v-if="!parent">
      Parent/Guardian Acknowledgement</button
    ><span class="acknowledged" v-if="parent">Acknowleged.</span>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      parent: false,
    }
  },
  methods: {
    sign() {
      this.parent = true
    },
  },
}
</script>

<style scoped></style>
