<template lang="pug">
div.article-container
  nuxt-link.back-to-root-button(to="/") 👈
  p.article-date {{ createdAt }}
  h1.article-title {{ article.fields.title }}
  div.article-body-container
    vue-markdown.article-body {{ article.fields.body }}
    span.article-category # {{ article.fields.category }}
  author-info
</template>

<script>
import { createClient } from '~/plugins/contentful.js'
import VueMarkdown from 'vue-markdown'
import clipStr from '~/utils/clip-str'
import h2p from 'html2plaintext'
import moment from 'moment'
import AuthorInfo from '../../components/AuthorInfo'

const client = createClient()
export default {
  components: {
    VueMarkdown,
    AuthorInfo
  },
  transition: 'fade-in',
  props: {
    id: {
      type: String,
      default: ''
    }
  },
  asyncData({ env, params }) {
    return client
      .getEntry(params.id)
      .then(entrie => {
        return {
          article: entrie
        }
      })
      .catch(console.error)
  },
  computed: {
    createdAt() {
      return moment(new Date(this.article.sys.createdAt)).format('YYYY/MM/DD')
    }
  },
  head() {
    const description = clipStr(
      h2p(this.article.fields.body).replace(/\r?\n/g, ''),
      400
    )
    return {
      title: this.article.fields.title,
      meta: [
        { hid: 'description', name: 'description', content: description },
        {
          hid: 'og:title',
          property: 'og:title',
          content: this.article.fields.title
        },
        {
          hid: 'og:description',
          property: 'og:description',
          content: description
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.article-container {
  max-width: 800px;
  margin: 0 auto;
  margin-top: 50px;
  margin-bottom: 50px;
  .back-to-root-button {
    font-size: 20px;
  }
  .article-date {
    font-size: 1.6rem;
    color: rgb(57, 72, 85);
    text-align: left;
    margin-bottom: 5px;
  }
  .article-title {
    font-size: 3rem;
    font-weight: bold;
    color: #9a4dc9;
  }
  .article-body-container {
    .article-body {
      margin-top: 50px;
    }
  }
  .article-category {
    background-color: #606c76;
    border: 0.1rem solid #606c76;
    border-radius: 0.4rem;
    color: #ffffff;
    display: inline-block;
    padding: 0.2rem 0.3rem;
    font-size: 1.2rem;
    // font-weight: bold;
    margin-bottom: 1px;
    // margin-left: 4px;
  }
}

@media screen and (max-width: 768px) {
  .article-container {
    .article-title {
      font-size: 2rem;
      font-weight: bold;
      color: #9a4dc9;
    }
  }
}
</style>
