<template>
  <p>Reaction Time: {{ score / 1000 }} ms</p>
</template>

<script>
export default {
    props: [ "score" ],
    methods: {
    }
}
</script>

<style>

</style>