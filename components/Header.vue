<template lang="pug">
div
  header
    div.site-title
      nuxt-link.site-title__link(to="/")
        vue-typer(text="toruokada.tokyo" :repeat='0')
    div.site-description
      p okachanによるブログ

</template>

<script>
if (process.browser) {
  var VueTyper = require('vue-typer').VueTyper
}
export default {
  components: {
    VueTyper
  }
}
</script>


<style lang="scss" scoped>
.site-title {
  font-size: 3.2rem;
  line-height: 1.3;
  font-weight: bold;
  text-align: center;
  &__link {
    text-decoration: none;
    color: inherit;
    opacity: 1;
    &:hover {
      opacity: 0.9;
    }
  }
}
.site-description p {
  font-size: 1.8rem;
  margin-top: 5px;
  text-align: center;
}
</style>
