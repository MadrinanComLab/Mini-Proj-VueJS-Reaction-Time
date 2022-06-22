<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
      Hit me!
  </div>
</template>

<script>
export default {
    props: [ "delay" ],
    data() {
        return {
            showBlock: false,
            timer: null,
            reactionTime: 0 // THIS WILL MEASURE HOW FAST THE USER CLICK THE GREEN BLOCK
        }
    },

    // VUE LIFECYCLE HOOK: MOUNTED
    mounted() { // THIS IS HOW TO CALL HOOK LIFECYCLE
        // TIMER WILL BE INITIALIZED HERE
        setTimeout(() => {
            this.showBlock = true
            this.startTimer() // INITIALIZING TIMER FOR GREEN BLOCK
        }, this.delay) // this.delay IS THE PASSED DATA IN PROPS
    },

    methods: {
        startTimer() { // THIS WILL BE CALLED ONCE THE GREEN BLOCK WAS DISPLAYED
            this.startTimer = setInterval(() => {
                this.reactionTime += 10
            }, 10)
        },

        stopTimer() { // THIS WILL BE CALLED ONCE THE USER CLICK THE GREEN BLOCK
            clearInterval(this.timer)
            this.$emit("end", this.reactionTime) // USING THIS WE'RE ABLE TO SEND THE VALUE OF reactionTime TO App.vue
        }
    },
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: #0FAF87;
        color: #FFF;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }
</style>