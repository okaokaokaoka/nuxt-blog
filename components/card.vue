<template lang="pug">
div
  article.card-wrapper
    nuxt-link.text-grey(:to="{ name: 'blog-slug', params: { slug: id　}}")
      p.card-title {{ title }}
      //- TODO: dateの加工が必要
      p.card-date {{ createdAt }}
</template>

<script>
import moment from 'moment'

export default {
  props: {
    title: {
      type: String,
      default: ''
    },
    id: {
      type: String,
      default: ''
    },
    date: {
      type: String,
      default: ''
    }
  },
  computed: {
    createdAt() {
      return moment(new Date(this.date)).format('YYYY/MM/DD')
    }
  }
}
</script>

<style lang="scss" scoped>
.card-wrapper {
  .card-title {
    font-size: 2rem;
    font-weight: bold;
    margin-bottom: 1px;
  }
}

@media screen and (max-width: 768px) {
  .card-wrapper {
    .card-title {
      font-size: 2rem;
      font-weight: bold;
      margin-bottom: 1px;
    }
  }
}
</style>
