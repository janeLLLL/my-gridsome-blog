<template>
  <Layout>

  </Layout>
</template>

<page-query>
query ($page: Int) {
  posts: allStrapiBlogs(perPage: 5, page: $page) @paginate {
    pageInfo {
      totalPages
      currentPage
    }
    edges {
      node {
        id
        title
        created_at
        // user {
        //   id
        //   username
        // }
        tags {
          id
          title
        }
      }
      
    }
  }

  general: allStrapiGeneral{
    edges {
      node {
        id
        title
        subtitle
        cover{
          url
        }
      }
    }
  }
}
</page-query>

<script>
import { Pager } from "gridsome";
export default {
  components: {
    Pager,
  },
  metaInfo: {
    title: "Hello, world!",
  },
};
</script>

<style>
</style>
