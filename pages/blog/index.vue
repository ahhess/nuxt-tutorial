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
  
  asyncData({ $axios, $config: { baseURL } }) {
    return $axios
      .get(`${baseURL}/posts`)
      .then((response) => {
        return { posts: response.data };
      });
  },

  data() {
    return {};
  },

  layout: "blog",
};
</script>