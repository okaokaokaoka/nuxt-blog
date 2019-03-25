<template lang="pug">
div.article-container
  //- nuxt-link.back-to-root-button(to="/") 👈
  h1.article-title {{ article.fields.title }}
  p.article-date {{ createdAt }}
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
  margin-top: 60px;
  margin-bottom: 50px;
  .back-to-root-button {
    font-size: 20px;
  }
  .article-date {
    font-size: 1.4rem;
    color: rgb(57, 72, 85);
    text-align: left;
    margin-bottom: 5px;
  }
  .article-title {
    font-size: 1.8rem;
    font-weight: bold;
    letter-spacing: 0.04em;
    margin-bottom: 10px;
    color: #9a4dc9;
  }
  .article-body-container {
    .article-body {
      margin-top: 40px;
      line-height: 1.8;
    }
  }
  .article-category {
    background-color: #606c76;
    border: 0.1rem solid #606c76;
    border-radius: 0.2rem;
    color: #ffffff;
    display: inline-block;
    padding: 0.1rem 0.4rem;
    font-size: 1.2rem;
    margin-bottom: 1px;
  }
}
@media screen and (min-width: 768px) {
  .article-container {
    .article-title {
      font-size: 2.2rem;
    }
    .article-date {
      font-size: 1.6rem;
    }
  }
}
</style>
