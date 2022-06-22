<template>
  <div class="block" v-if="showBlock">
      Hit me!
  </div>
</template>

<script>
export default {
    props: [ "delay" ],
    data() {
        return {
            showBlock: false
        }
    },

    // VUE LIFECYCLE HOOK: MOUNTED
    mounted() { // THIS IS HOW TO CALL HOOK LIFECYCLE
        // TIMER WILL BE INITIALIZED HERE
        setTimeout(() => {
            this.showBlock = true
        }, this.delay) // this.delay IS THE PASSED DATA IN PROPS
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