<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p class="rank">{{ rank }}</p>
</template>

<script>
export default {
    props: [ "score" ],

    data() {
        return {
            rank: null
        }
    },

    mounted() {
        if (this.score < 250) return this.rank = "Excellent!"
        else if (this.score < 400) return this.rank = "Ok, not bad"
        else return this.rank = "Bruh, What a slow poke"
    },

    methods: {
    }
}
</script>

<style>
    .rank {
        font-size: 1.4em;
        color: #0FAF87;
        font-weight: bold;
    }
</style>