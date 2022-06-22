<!--/ 
  THE NET NINJA DISCUSSED ABOUT THE LIFECYCLE HOOKS,  HERE IS THE DOCUMENTATION FROM VUE:
  https://vuejs.org/guide/essentials/lifecycle.html#lifecycle-diagram
/-->

<template>
  <h1>MadrinanComLab Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button><!--/ THIS BUTTON WILL BE DISABLED IF THE USER STARTED THE GAME... /-->

  <!--/ BLOCK COMPONENT WILL BE DISPLAY IF THE isPlaying IS true /-->
  <Block v-if="isPlaying" :delay="delay" @end="endGame"/><!--/ NOTE: @end IS HOW WE LISTEN TO CUSTOM EVENT. /-->
  <!--/ <p v-if="score">Reaction Time: {{ score }} ms</p> /-->
  <Results v-if="score" :score="score"/>
</template>

<script>
import Block from "./components/Block.vue"
import Results from "./components/Results.vue"

export default {
  name: 'App',
  components: { Block, Results }, // DON'T FOGET TO REGISTER YOUR IMPORTED COMPONENTS HERE...

  data() {
    return {
      isPlaying: false, // DETECT IF THE USER IS PLAYING...
      delay: null,
      score: null
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000 // GENERATING A RANDOM TIME DURATION FOR DELAY (MIN. TIME: 2 SEC | MAX. TIME: 7 SEC)
      this.isPlaying = true
      this.score = null // SINCE WE USE THE VALUE OF SCORE TO HIDE THE RESULT, WE MUST SET THIS TO NULL SO ONCE USER PLAYS AGAIN THE SCORE WILL BE RESET
    },

    endGame(reactionTime) { // WE ARE ABLE TO GET reactionTime AS A PARAMETER BECAUSE WE DEFINE THE this.reactionTime AS 2ND ARGUMENT IN this.$emit()
      this.score = reactionTime
      this.isPlaying = false // WE GOT THE SCORE THEN THE USER IS NOW DONE PLAYING
    },
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #444;
  margin-top: 60px;
}
</style>
