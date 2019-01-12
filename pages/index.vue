<template lang="pug">
div
  section.container
    card(v-for="i in 5" :key="i")
</template>

<script>
import Card from '../components/card'

export default {
  components: {
    Card
  }
}
</script>

<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
</style>
