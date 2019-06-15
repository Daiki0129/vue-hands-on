<template>
  <div id="app">
    <p>step{{step}}</p>
    <OyasumiHeader/>
    <InputQuestion v-if="step == 0" key="start" @start="handleStart"/>
    <OyasumiResult :questions="questions" :step="step"/>
  </div>
</template>

<script>
import OyasumiHeader from "./components/OyasumiHeader.vue";
import InputQuestion from "./components/InputQuestion.vue";
import OyasumiResult from "./components/OyasumiResult.vue";

export default {
  name: "app",
  components: {
    OyasumiHeader,
    InputQuestion,
    OyasumiResult
  },
  data() {
    return {
      step: 0,
      questions: {
        name: "",
        title: 1
      }
    };
  },
  methods: {
    handleStart(startData) {
      console.log("start");
      console.log(startData);
      this.questions.name = startData.name;
      this.questions.title = startData.title;
      this.step++;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  /* margin-top: 60px; */
}
</style>