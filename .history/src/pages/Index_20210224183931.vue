<template>
  <Layout>
    <!-- Page Header -->
    <header
      class="masthead"
      :style="
        $page.homes.edges[3].node.cover
          ? {
              backgroundImage: `url(http://106.75.15.148:1337${$page.homes.edges[3].node.cover.url})`,
            }
          : ''
      "
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="site-heading">
              <h1>{{ $page.homes.edges[3].node.title }}</h1>
              <span class="subheading">{{ $page.homes.edges[3].node.subtitle }}</span>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <div
            class="post-preview"
            v-for="edge in $page.posts.edges"
            :key="edge.node.id"
          >
            <g-link :to="'/post/' + edge.node.id">
              <h2 class="post-title">
                {{ edge.node.title }}
              </h2>
            </g-link>
            <p class="post-meta">
              Posted by
              <a href="#">{{ edge.node.user.username }}</a>
              on {{ edge.node.created_at }}
            </p>
            <p>
              <span v-for="tag in edge.node.tags" :key="tag">
                <g-link :to="'/tag/' + tag.id" href="">{{ tag.title }}</g-link> / 
              </span>
            </p>
            <hr />
          </div>
        </div>
      </div>
    </div>
    <Pager :info="$page.posts.pageInfo" />
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
        user {
          id
          username
        }
        tags {
          id
          title
        }
      }
    }
  }

    homes: allStrapiHomes {
    edges {
      node {
        id,
        subtitle,
        title,
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
