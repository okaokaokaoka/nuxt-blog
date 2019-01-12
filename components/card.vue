<template lang="pug">
div
  article.card
    nuxt-link.wrapper(:to="{ name: 'blog-slug'}")
      h1.card_title 記事１
      p.card_text 記事の内容。hogehogehogehogehoge
      p.card_date 2018/8/2
</template>
