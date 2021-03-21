<template>
    <div>
        <h1>({{ post.id }}) {{ post.title }}</h1>
        <div>{{ post.body }}</div>
    </div>
</template>

<script>
export default {
  asyncData({ $axios, route }) {
    //   console.log(route.params.id)
    return $axios
      .get(`http://jsonplaceholder.typicode.com/posts/${route.params.id}`)
      .then((response) => {
        // console.log("server side");
        return { post: response.data };
      });
  },

  data() {
    return {};
  },

  layout: 'blog',
};
</script>