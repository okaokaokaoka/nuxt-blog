<template lang="pug">
div
  article.card-wrapper
    nuxt-link.text-grey(:to="{ name: 'blog-slug', params: { slug: slug, id: id }}")
      p.card-title {{ title }}
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
    },
    slug: {
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
    font-size: 1.8rem;
    font-weight: bold;
    margin-bottom: 1px;
  }
  .card-date {
    font-size: 1.4rem;
  }
}

@media screen and (min-width: 768px) {
  .card-wrapper {
    .card-title {
      font-size: 2.2rem;
      font-weight: bold;
      margin-bottom: 1px;
    }
    .card-date {
      font-size: 1.6rem;
    }
  }
}
</style>
