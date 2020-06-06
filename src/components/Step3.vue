<template>
  <div>
    <h2>Step 3</h2>
    <h3>Athletic Handbook</h3>
    <ol>
      <li>
        I/We acknowledge that the participant is assuming a certain risk of
        being injured; that even with the best coaching, use of the most advance
        protective equipment and strict observance of rules, injuries are still
        a possibility in organized athletics. On rare occasions, these injuries
        can be so severe as to result in total disability, paralysis or even
        death.
      </li>
      <li>
        I/We, as parent(s), agree to abide by and support the rules established
        by the coaches, the IHSAA and the school and to encourage and assist
        my/our child at the same time.
      </li>
      <li>
        Parent(s) - Guardian(s) and athletes are encouraged and expected to read
        and become familiar with those items of information included in the
        Covenant Christian High School Athletic Handbook. Your acknowledgement
        indicates the following:
      </li>
      <ol style="list-style-type: lower-alpha;">
        <li>
          Permission for my son/daughter to participate in any inter-school
          sports except
          <input type="text" v-model="exception" />.
        </li>
        <li>
          An awareness of the school’s policies as noted in the Student Handbook
          and Athletic Handbook, at Coaches’ Meeting and in any and all
          materials distributed by any member of the school faculty relative to:
          <table>
            <tr>
              <td>Injuries</td>
              <td>Expenses</td>
              <td>Insurance</td>
              <td>Academics</td>
            </tr>
            <tr>
              <td>Training &amp; Conduct Rules</td>
              <td>Disciplinary Codes</td>
              <td>Awards</td>
              <td>Other Handbook Items</td>
            </tr>
          </table>
        </li>
      </ol>
    </ol>
    <button @click="sign(1)" v-if="!parent1">
      Parent/Guardian Acknowledgement</button
    ><span class="acknowledged" v-if="parent1">Acknowleged.</span>
    <h3>
      Student Application and Parent/Guardian Authorization for Participation
    </h3>
    <p>
      The undersigned certify they have read the Covenant Christian High School
      Athletic Handbook and understand the eligibility and conduct guidelines
      contained therein for student and parent. The student hereby makes
      application for the privilege to participate in the interscholastic
      Athletic Program sponsored by Covenant Christian High School and the
      IHSAA. It is understood that in order to be eligible to participate the
      student must comply with all requirements of the handbook.
    </p>
    <p>
      **The undersigned student and parent/guardian further consent to the
      release by law enforcement and/or juvenile court authorities to school
      officials of records and other information indicating use or possession of
      alcoholic beverages or illegal drugs or other activity involving the
      courts and police by the student recognize that such record and
      information may be considered by school officials in determining a
      student’s eligibility to participate in the Athletic Program.
    </p>
    <button @click="sign(2)" v-if="!parent2">
      Parent/Guardian Acknowledgement</button
    ><span class="acknowledged" v-if="parent2">Acknowledged.</span>
    <br />
    <br />
    <button @click="sign(3)" v-if="!student">
      Student/Athlete Acknowledgement</button
    ><span class="acknowledged" v-if="student">Acknowledged.</span>
    <p>
      <i
        >Student/Athlete may not participate in practices or contests until this
        form is on file with the Covenant Christian High School Athletic
        Office.</i
      >
    </p>
    <p>
      <i
        >**The School will not only pursue the acquisition of legal records in
        the event that the student is involved in a code violation, or there is
        reasonable suspicion to warrant an investigation. This is not for
        purposes of random checks without warranted suspicion. A record search
        with authorities will only be instigated after the parents of the
        athlete have been notified.</i
      >
    </p>
  </div>
</template>

<script>
export default {
  data: () => {
    return {
      exception: '',
      parent1: false,
      parent2: false,
      student: false,
    }
  },
  methods: {
    sign(i) {
      switch (i) {
        case 1:
          this.parent1 = true
          break
        case 2:
          this.parent2 = true
          break
        case 3:
          this.student = true
          break
      }
    },
  },
}
</script>

<style scoped>
table {
  border-collapse: collapse;
}
td {
  border: 1px solid #000;
  padding: 1vw;
}
</style>
