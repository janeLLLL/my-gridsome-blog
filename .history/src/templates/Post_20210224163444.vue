<template>
  <Layout>
    <!-- Page Header -->
    <header
      class="masthead"
      :style="
        $page.strapiBlogs.cover
          ? {
              backgroundImage: `url(http://106.75.15.148:1337${$page.strapiBlogs.cover.url})`,
            }
          : ''
      "
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="post-heading">
              <h1>{{ $page.strapiBlogs.title }}</h1>
              <span class="meta"
                >Posted by
                <a href="#">{{ $page.strapiBlogs.user.username }}</a>
                on {{ $page.strapiBlogs.created_at }}</span
              >
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Post Content -->
    <article>
      <div class="container">
        <div class="row">
          <div
            class="col-lg-8 col-md-10 mx-auto"
            v-html="mdToHtml($page.strapiBlogs.content)"
          ></div>
        </div>
      </div>
    </article>
  </Layout>
</template>

<page-query>
query ($id: ID!) {
  strapiBlogs (id: $id){
    user{
      username
    }
    id
    title
    content
    created_at
    cover{
      url
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