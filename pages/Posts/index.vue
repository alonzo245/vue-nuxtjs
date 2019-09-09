<template>
  <div>
    <SearchPosts v-on:search-text="searchText" />
    <Post v-for="post in posts" :key="post.id" :id="post.id" :post="post.title" />
  </div>
</template>

<script>
import axios from "axios";
import Post from "../../components/Post";
import SearchPosts from "../../components/SearchPosts";

export default {
  components: {
    Post
  },
  data() {
    return {
      posts: []
    };
  },
  async created() {
    const config = {
      headers: {
        Accept: "applkication/json"
      }
    };
    try {
      // let posts = localStorage.getItem("posts") || [];
      // let posts = localStorage.getItem("posts") || [];
      // if (posts.length === 0) {
      const res = await axios.get("https://jsonplaceholder.typicode.com/posts");
      // localStorage.setItem("posts", JSON.stringify(res.data));
      // }
      // this.posts = JSON.parse(posts);
      // console.log(JSON.parse(posts));
      this.posts = res.data;
    } catch (error) {
      console.log(error);
    }
  },
  methods: {
    async searchText(text) {
      const config = {
        headers: {
          Accept: "applkication/json"
        }
      };
      try {
        const res = await axios.get(
          "https://jsonplaceholder.typicode.com/posts"
        );
        this.posts = res.data;
      } catch (error) {
        console.log(error);
      }
    }
  },
  head() {
    return {
      title: "Posts",
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