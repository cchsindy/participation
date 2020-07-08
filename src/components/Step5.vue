<template>
  <div>
    <h2>Step 5</h2>
    <h3>Student Transportation</h3>
    <p>
      Due to the high cost of hiring transportation services, Covenant Christian
      High School often needs help in transporting student on field trips or for
      sporting events. Parents, coaches and staff have been generous in
      providing transportation assistance. All volunteer drivers are adults and
      have completed a Volunteer Driver Form to reduce the liability of the
      school and volunteer drivers by allowing Covenant to be proactive in the
      selection of adult drivers.
    </p>
    <p>
      Volunteer drivers certify that they have adequate insurance, a valid
      license, and will only transport the number of students in accordance with
      the manufacturer’s rated seating capacity for the vehicle. Students will
      not be allowed to transport other students to school sponsored activities
      unless volunteer driver forms are completed.
    </p>
    <p>
      I, the undersigned parent or guardian, hereby consent for my child to be
      driven to field trips and sporting events by volunteer drivers approved by
      Covenant Christian High School effective August 1 - June 30 of the current
      school year.
    </p>
    <p>
      I certify that my child is able to participate in the activities required
      for participation in these events. If my child has medical conditions
      which may be relevant to a physician in the event of an emergency, I have
      listed them below. In the event an emergency occurs, I may be reached at
      the telephone number listed below. If I cannot be reached, I hereby
      authorize the adult supervisors, and sponsors to make emergency medical
      decisions for my child. If there are any activities in which I do not want
      my child to be involved, I have listed them below.
    </p>
    <p>
      I UNDERSTAND AND HEREBY AGREE TO ASSUME ALL OF THE RISKS WHICH MAY BE
      ENCOUNTERED ON SAID ACTIVITY, INCLUDING ACTIVITIES PRELIMINARY AND
      SUBSEQUENT THERETO. I do hereby agree to hold Covenant Christian High
      School and its agents and employees, harmless from any and all liability,
      actions, causes of actions, claims, expenses and damages on account of
      injury to my child or property, even injury resulting in death, which I
      now have or which may arise in the future in connection with the activity
      or participation in my other associated activities.
    </p>
    <p>
      I expressly agree that this release, waiver and indemnity agreement is
      intended to be broad and inclusive as permitted by the law of the State of
      Indiana, and that if any portion thereof is held invalid, it is agreed
      that the balance shall, notwithstanding, continue in full legal force and
      effect. This release contains the entire agreement between the parties
      hereto, and the terms of this release are contractual and not a mere
      recital.
    </p>
    <p>
      I further state that i have carefully read the foregoing release and know
      the contents thereof, and I sign this release as my own free act. This is
      a legally binding agreement which I have read and understand.
    </p>
    <button @click="sign" v-if="!parent">Parent/Guardian Acknowledgement</button
    ><span class="acknowledged" v-if="parent">Acknowledged.</span>
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
