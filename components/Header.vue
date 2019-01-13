<template lang="pug">
div
  header
    div.site-title
      nuxt-link.site-title__link(to="/") toruokada.tokyo
    div.site-description
      p okachanによるブログ

</template>

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
