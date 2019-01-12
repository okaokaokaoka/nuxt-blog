<template lang="pug">
  section.slug
    h1.slug-title {{ article.fields.title }}
    p.slug-date {{ article.sys.updatedAt }}
    vue-markdown {{ article.fields.body }}
</template>

<script>
import { createClient } from '~/plugins/contentful.js'
import VueMarkdown from 'vue-markdown'

const client = createClient()
export default {
  components: {
    VueMarkdown
  },
  props: {
    id: {
      type: String,
      default: ''
    }
  },
  transition: 'slide-left',
  async asyncData({ env, params }) {
    return await client
      .getEntry(params.slug)
      .then(entrie => {
        return {
          article: entrie
        }
      })
      .catch(console.error)
  }
}
</script>

<style lang="scss" scoped>
.slug {
  max-width: 800px;
  margin: 0 auto;
}
.slug_title {
  font-size: 2rem;
  font-weight: bolder;
}
.slug_date {
  font-size: 1rem;
  color: rgb(57, 72, 85);
  text-align: right;
}
</style>
