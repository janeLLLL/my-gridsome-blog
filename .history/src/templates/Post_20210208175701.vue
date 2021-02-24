<template>
  <Layout>

  </Layout>
</template>

<page-query>
query ($id: ID!) {
  strapiBlogs (id: $id){
    // user{
    //   username
    // }
    id
    title
    content
    created_at
    cover{
      url
    }
    tags{
      id
      title
    }
  }
}
</page-query>

<script>
var MarkdownIt = require("markdown-it");
const md = new MarkdownIt();

export default {
  metaInfo: {
    title: "文章",
  },
  name: "HomePage",
  methods: {
    mdToHtml(markdown) {
      return md.render(markdown);
    },
  },
};
</script>

<style>
</style>