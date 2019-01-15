<template lang="pug">
div.about-wrapper
  div.profile-wapper
    h2 # Profile
    p - name: Toru Okada
    p - nickname: Okachan
    p - age: 22
    p - birthplace: Saitama
    p - university: Osaka univ.
  div.links-wrapper
    h2 # Links
    a(href="https://twitter.com/toru__okada") - Twitter(@toru__okada)
    a(href="https://github.com/okaokaokaoka") - Github(okaokaokaoka)
    a(href="https://www.facebook.com/okaokaokatoru") - Facebook(Toru Okada)
    a(href="mailto:toruhandbell0424@gmail.com?subject=I love you.") - Mail
</template>

<style lang="scss" scoped>
.about-wrapper {
  margin-top: 5rem;
  .profile-wapper {
    p {
      margin-bottom: 1rem;
    }
  }
  .links-wrapper {
    margin-top: 3rem;
    a {
      display: block;
      margin-bottom: 1rem;
    }
  }
}

@media screen and (min-width: 768px) {
  .about-wrapper {
    margin-top: 0;
    padding: 10rem;
  }
}
</style>
