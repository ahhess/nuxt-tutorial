<template>
    <div>
        <h1>Blog page</h1>
        <li v-for="post in posts" :key="post.id">
            <nuxt-link :to="`/blog/${post.id}`">{{post.title}}</nuxt-link>
        </li>
    </div>
</template>

<script>
export default {
  asyncData({ $axios }) {
    return $axios
      .get("http://jsonplaceholder.typicode.com/posts")
      .then((response) => {
        // console.log("server side");
        return { posts: response.data };
      });
  },

  data() {
    return {};
  },

  layout: "blog",
};
</script>