<template>
  <h1>Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">play</button>
  <BlockBox v-if="isPlaying" :delay="delay" @end="endGame" />
  <ResultsBox v-if="showResults" :results="score" />
</template>

<script>
import BlockBox from "./components/BlockBox.vue";
import ResultsBox from "./components/ResultsBox.vue";

export default {
  name: "App",
  components: { BlockBox, ResultsBox },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResults: false,
    };
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResults = false;
    },
    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResults = true;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #444;
  text-align: center;
}
</style>
