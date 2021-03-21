<template>
  <div></div>
</template>

<page-query>
query ($id: ID!) {
  markdownPage(id: $id) {
    id
    path
    title
    description
    excerpt
  }
}
</page-query>

<script>
export default {
  created(){
    // window.location = `${this.$page.markdownPage.path}`
    this.$router.push(this.$page.markdownPage.path);
  },
  metaInfo() {
    const title = this.$page.markdownPage.title;
    const description = this.$page.markdownPage.description || this.$page.markdownPage.excerpt;

    return {
      title: title,
      meta: [
        // { 'http-equiv': 'refresh', content: `0; URL=${this.$page.markdownPage.path}`},
        {
          name: 'description',
          content: description
        },
        {
          key: 'og:title',
          name: 'og:title',
          content: title,
        },
        {
          key: 'twitter:title',
          name: 'twitter:title',
          content: title,
        },
        {
          key: 'og:description',
          name: 'og:description',
          content: description,
        },
        {
          key: 'twitter:description',
          name: 'twitter:description',
          content: description,
        },
      ],
      link: [
          { rel: 'canonical', href: `https://wysc.us.to${this.$page.markdownPage.path}` }
      ]
    }
  }
}
</script>

<style>
</style>