<template>
  <h1>Ninja reaction timer</h1>
  <button @click="start" :disabled="isPlaying" class="playBtn">Play</button>
  <Results v-if="score" :score="score" />
  <Block v-if="isPlaying" :delay="delay" @end="endGame" />
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  components: {
    Block,
    Results
  },
  data() {
    return {
      isPlaying: false,
      delay: null,
      score: null,
    }
  },
  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000
      this.isPlaying = true
      this.score = null
    },
    endGame(reactionTime) {
      this.score = reactionTime
      this.isPlaying = false
    }
  },
}
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

.playBtn {
  color: #fff;
  background: rgba(44, 156, 113, 1);
  border: none;
  padding: 0.5rem 1rem;
  border-radius: 4px;
  cursor: pointer;
}

.playBtn:disabled {
  background: rgba(44, 156, 113, 0.2);
  cursor: not-allowed;
}
</style>
