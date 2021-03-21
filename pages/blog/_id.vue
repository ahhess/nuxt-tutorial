<template>
    <div>
        <h1>({{ post.id }}) {{ post.title }}</h1>
        <div>{{ post.body }}</div>
    </div>
</template>

<script>
export default {
  asyncData({ $axios, route, $config: { baseURL } }) {
    return $axios
      .get(`${baseURL}/posts/${route.params.id}`)
      .then((response) => {
        return { post: response.data };
      });
  },

  data() {
    return {};
  },

  layout: 'blog',
};
</script>