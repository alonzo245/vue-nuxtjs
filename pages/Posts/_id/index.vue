<template>
  <div>
    <nuxt-link to="/posts">Back to posts</nuxt-link>
    <br>
    <small>Post id: {{$route.params.id}}</small>
    <h2>{{post.title}}</h2>
    <article>{{post.body}}</article>
    <hr />
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      post: {}
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "applkication/json"
      }
    };

    try {
      const res = await axios.get(
        `https://jsonplaceholder.typicode.com/posts/${this.$route.params.id}`,
        config
      );
      this.post = res.data;
      console.log(res);
    } catch (error) {
      console.log(error);
    }
  },
  head() {
    return {
      title: this.post.title,
      meta: [
        {
          hid: "description",
          name: "Posts  description",
          content: "Posts  description"
        }
      ]
    };
  }
};
</script>

<style>
</style>
