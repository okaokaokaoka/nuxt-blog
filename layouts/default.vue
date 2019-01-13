<template lang="pug">
div.app-container
  Header
  nuxt
</template>

<script>
import Header from '../components/Header'

export default {
  components: {
    Header
  }
}
</script>


<style lang="scss">
.app-container {
  max-width: 1000px;
  margin-right: auto;
  margin-left: auto;
  padding: 20px;
}
</style>
