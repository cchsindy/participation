<template>
  <div id="app">
    <h1>Athletic Participation</h1>
    <component :is="currentStep" />
    <button @click="nextStep">Next Step</button>
  </div>
</template>

<script>
import Step1 from "@/components/Step1";
import Step2 from "@/components/Step2";
import Step3 from "@/components/Step3";

export default {
  name: "App",
  components: {
    Step1,
    Step2,
    Step3
  },
  data: () => {
    return {
      currentIndex: 1,
      currentStep: "Step1"
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
