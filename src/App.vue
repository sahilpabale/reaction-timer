<template>
  <h1>Reaction Timer</h1>
  <br />
  <button class="play-btn" :disabled="isPlaying" @click="start">
    Play
  </button>
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
  <Results v-if="showResult" :score="score" />
</template>

<script>
import Block from "./components/Block";
import Results from "./components/Results";

export default {
  name: "App",

  components: {
    Block,
    Results,
  },

  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
      showResult: false,
    };
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
      this.showResult = false;
    },

    endGame(reactionTime) {
      this.score = reactionTime;
      this.isPlaying = false;
      this.showResult = true;
    },
  },
};
</script>

<style>
#app {
  font-family: "Inter", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}

h1 {
  border-bottom: 3px solid crimson;
  display: inline-block;
  padding-bottom: 5px;
}

.play-btn {
  background: crimson;
  height: 2rem;
  width: 6rem;
  color: white;
  border: 2px solid transparent;
  border-radius: 5px;
  cursor: pointer;
}

.play-btn:hover {
  background: transparent;
  height: 2rem;
  width: 6rem;
  color: crimson;
  border: 2px solid crimson;
  border-radius: 5px;
  cursor: pointer;
}
</style>
