<template>
  <Layout>
    <h1 class="blog-title">
      Welcome my awesome blog
    </h1>
    <p>I love Vue.js so I write about it.</p>

    <div class="articles-list">
      <h2 class="article-list__section-heading">New Articles</h2>
      <div class="article-list__item" v-for="({ node: article }, index) in $page.allBlogPost.edges" :key="index">
        <h3>
          <g-link :to="article.path">{{ article.title }}</g-link>
          <!-- g-link is the Gridsome equivalent of router-link for Vue, but with a some magic  ✨ -->
        </h3>
        <p>
          Published on <strong>{{ article.date }}</strong>
        </p>
        <p>{{ article.description }}</p>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query {
  allBlogPost (filter:{ published: {eq: true } } ) {
    edges{
      node{
        path,
        title,
        date(format: "DD MMM YYYY"),
      	timeToRead,
        description,
        content,
      }
    }
  }
}
</page-query>

<script>
export default {
  metaInfo: {
    title: 'Hello, world!',
  },
};
</script>

<style></style>
