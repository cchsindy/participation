<template>
  <div>
    <h2>Step 4</h2>
    <h3>Concussion and Sudden Cardiac Arrest</h3>
    <p>
      IC 20-34-7 and IC 20-34-8 require schools to distribute information sheets
      to inform and educate student athletes and their parents on the nature and
      risk of concussion, head injury and sudden cardiac arrest to student
      athletes, including the risks of continuing to play after concussion or
      head injury. These laws require that each year, before beginning practice
      for an interscholastic sport, a student athlete and the student athlete’s
      parents must be given an information sheet, and both must sign and return
      a form acknowledging receipt of the information to the student athlete’s
      coach.
    </p>
    <p>
      IC 20-34-7 states that an interscholastic student athlete, in grades 5-12,
      who is suspected of sustaining a concussion or head injury in a practice
      or game, shall be removed from play at the time of injury and may not
      return to play until the student athlete has received a written clearance
      from a licensed health care provider trained in the evaluation and
      management of concussions and head injuries, and at least twenty-four
      hours have passed since the injury occurred.
    </p>
    <p>
      IC 20-34-8 states that a student athlete who is suspected of experiencing
      symptoms of sudden cardiac arrest shall be removed from play and may not
      return to play until the coach has received verbal permission from a
      parent or legal guardian for the student athlete to return to play. Within
      twenty-four hours, this verbal permission must be replaced by a written
      statement from the parent or guardian.
    </p>
    <p>
      Parent/Guardian - please read the attached fact sheets regarding
      concussion and sudden cardiac arrest and ensure that your student athlete
      has also received and read these fact sheets. After reading these fact
      sheets, please ensure that you and your student athlete sign this form,
      and have your student athlete return this form to his/her coach.
    </p>
    <hr />
    <p>
      As a student athlete, I have received and read both of the fact sheets
      regarding concussion and sudden cardiac arrest. I understand the nature
      and risk of concussion and head injury to student athletes, including the
      risks of continuing to play after concussion or head injury, and the
      symptoms of sudden cardiac arrest.
    </p>
    <button @click="sign(1)" v-if="!student">
      Student/Athlete Acknowledgement</button
    ><span class="acknowledged" v-if="student">Acknowledged.</span>
    <p>
      I, as the parent or legal guardian of the above named student, have
      received and read both of the fact sheets regarding concussion and sudden
      cardiac arrest. I understand the nature and risk of concussion and head
      injury to student athletes, including the risks of continuing to play
      after concussion or head injury, and the symptoms of sudden cardiac
      arrest.
    </p>
    <button @click="sign(2)" v-if="!parent">
      Parent/Guardian Acknowledgement</button
    ><span class="acknowledged" v-if="parent">Acknowledged.</span>
    <br />
    <br />
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      student: false,
      parent: false,
    }
  },
  methods: {
    sign(i) {
      switch (i) {
        case 1:
          this.student = true
          break
        case 2:
          this.parent = true
          break
      }
    },
  },
}
</script>

<style scoped></style>
