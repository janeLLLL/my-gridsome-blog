<template>
  <Layout>
    <!-- Page Header -->
    <header
      class="masthead"
      :style="
        $page.homes.edges[2]
          ? {
              backgroundImage: `url(http://106.75.15.148:1337${$page.homes.edges[2].node.cover.url})`,
            }
          : ''
      "
    >
      <div class="overlay"></div>
      <div class="container">
        <div class="row">
          <div class="col-lg-8 col-md-10 mx-auto">
            <div class="site-heading">
              <h1>{{ $page.homes.edges[2].node.title }}</h1>
              <span class="subheading">{{ $page.homes.edges[2].node.subtitle }}</span>
            </div>
          </div>
        </div>
      </div>
    </header>

    <!-- Main Content -->
    <div class="container">
      <div class="row">
        <div class="col-lg-8 col-md-10 mx-auto">
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Saepe
            nostrum ullam eveniet pariatur voluptates odit, fuga atque ea nobis
            sit soluta odio, adipisci quas excepturi maxime quae totam ducimus
            consectetur?
          </p>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Eius
            praesentium recusandae illo eaque architecto error, repellendus
            iusto reprehenderit, doloribus, minus sunt. Numquam at quae
            voluptatum in officia voluptas voluptatibus, minus!
          </p>
          <p>
            Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aut
            consequuntur magnam, excepturi aliquid ex itaque esse est vero natus
            quae optio aperiam soluta voluptatibus corporis atque iste neque sit
            tempora!
          </p>
        </div>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query  {
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
export default {
  name: 'AboutPage',
  metaInfo: {
    title: "About us",
  },
};
</script>
