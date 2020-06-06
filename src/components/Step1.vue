<template>
  <div>
    <h2>Step 1</h2>
    <h3>Required Enrollment Forms</h3>
    <p>
      I have completed the Student Emergency Contacts, Student Medical
      Information, and Non-prescription Medication Permission forms in
      MySchoolApp.
    </p>
    <button @click="sign" v-if="!acknowledged">
      Parent/Guardian Acknowledgement</button
    ><span class="acknowledged" v-if="acknowledged">Acknowleged.</span>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      acknowledged: false,
    }
  },
  methods: {
    sign() {
      this.acknowledged = true
    },
  },
}
</script>

<style scoped></style>
