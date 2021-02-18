<template>
  <div class="container">
    <h1>All Posts</h1>
    <div v-for="post in posts">
      <h2>{{ post.title }}</h2>
      <p>Title: {{ post.title }}</p>
      <p>Body: {{ post.body }}</p>
      <router-link v-bind:to="`/posts/${post.id}`">More details</router-link>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      posts: []
    };
  },
  created: function() {
    axios.get("/api/posts").then((response) => {
      this.photos = response.data;
    });
  },
  methods: {}
};
</script>
