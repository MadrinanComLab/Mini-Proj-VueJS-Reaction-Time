<!--/ 
  THE NET NINJA DISCUSSED ABOUT THE LIFECYCLE HOOKS,  HERE IS THE DOCUMENTATION FROM VUE:
  https://vuejs.org/guide/essentials/lifecycle.html#lifecycle-diagram
/-->

<template>
  <h1>MadrinanComLab Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying">Play</button><!--/ THIS BUTTON WILL BE DISABLED IF THE USER STARTED THE GAME... /-->

  <!--/ BLOCK COMPONENT WILL BE DISPLAY IF THE isPlaying IS true /-->
  <Block v-if="isPlaying" :delay="delay"/>
</template>

<script>
import Block from "./components/Block.vue"

export default {
  name: 'App',
  components: { Block }, // DON'T FOGET TO REGISTER YOUR IMPORTED COMPONENTS HERE...

  data() {
    return {
      isPlaying: false, // DETECT IF THE USER IS PLAYING...
      delay: null,
    }
  },

  methods: {
    start() {
      this.delay = 2000 + Math.random() * 5000 // GENERATING A RANDOM TIME DURATION FOR DELAY (MIN. TIME: 2 SEC | MAX. TIME: 7 SEC)
      this.isPlaying = true
    }
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
