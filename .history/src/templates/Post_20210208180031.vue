<template>
  <Layout>

  </Layout>
</template>



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