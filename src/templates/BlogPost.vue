<template>
  <div>
    <Layout>
      <h1>{{ $page.post.title }}</h1>
      <p>
        Published on <strong>{{ $page.post.date }}</strong
        >, <strong>{{ $page.post.timeToRead }} min.</strong> read
      </p>
      <div v-html="$page.post.content"></div>
    </Layout>
  </div>
</template>

<page-query>
query blogPost ($path: String!) {
  post: blogPost (path: $path) {
    id
    title
    content
    date (format: "D MMMM YYYY")
    timeToRead
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.post.title,
    };
  },
};
</script>
