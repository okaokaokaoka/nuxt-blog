<template lang="pug">
div.author-info-container
  p.author-name Author
  div.author-links
    span - Twitter:
    a(href="https://twitter.com/toru__okada")  @toru__okada
    br
    span - Github: 
    a(href="https://github.com/okaokaokaoka")  okaokaokaoka
    br
    span - Facebook: 
    a(href="https://www.facebook.com/okaokaokatoru")  Toru Okada
  div.about-link
    nuxt-link(to="/about") More detail...
</template>

<script>
import VueMarkdown from 'vue-markdown'

export default {
  components: {
    VueMarkdown
  }
}
</script>

<style lang="scss" scoped>
.author-info-container {
  margin-top: 50px;
  padding: 1em;
  border: 1px solid #ccc;
  .author-name {
    margin-bottom: 5px;
  }
  .about-link {
    margin-top: 2rem;
  }
}
</style>
