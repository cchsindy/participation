<template>
  <div id="app">
    <h1>Athletic Participation</h1>
    <component :is="currentStep" />
    <button v-if="currentIndex < 5" @click="nextStep">Next Step</button>
  </div>
</template>

<script>
import Step0 from "@/components/Step0";
import Step1 from "@/components/Step1";
import Step2 from "@/components/Step2";
import Step3 from "@/components/Step3";
import Step4 from "@/components/Step4";
import Step5 from "@/components/Step5";

export default {
  name: "App",
  components: {
    Step0,
    Step1,
    Step2,
    Step3,
    Step4,
    Step5
  },
  data: () => {
    return {
      currentIndex: 0,
      currentStep: "Step0"
    };
  },
  methods: {
    nextStep() {
      this.currentIndex++;
      this.currentStep = "Step" + this.currentIndex;
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
