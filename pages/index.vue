<template lang="pug">
div
  section.container
    card(v-for="(post,i) in posts"
    :key="i"
    :title="post.fields.title"
    :id="post.sys.id"
    :date="post.sys.updatedAt")
</template>

<script>
import { createClient } from '~/plugins/contentful.js'
import Card from '~/components/Card'

const client = createClient()

export default {
  components: {
    Card
  },
  asyncData({ env, params }) {
    return client
      .getEntries(env.CTF_BLOG_POST_TYPE_ID)
      .then(entries => {
        return {
          posts: entries.items
        }
      })
      .catch(console.error)
  }
}
</script>

<style lang="scss">
.container {
  margin-top: 50px;
  max-width: 800px;
}

@media screen and (max-width: 768px) {
  .container {
    margin-top: 40px;
  }
}
</style>
