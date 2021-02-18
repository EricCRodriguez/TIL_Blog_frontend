<template>
  <div class="container">
    <h2>{{ post.name }}</h2>
    <p>Title: {{ post.title }}</p>
    <p>Body: {{ post.body }}</p>
    <button v-on:click="destroyPost(post)">Delete post</button>
    <router-link v-bind:to="`/posts/${post.id}/edit`">Edit post</router-link>
    <router-link to="/posts">Back to all posts</router-link>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: function() {
    return {
      post: {}
    };
  },
  created: function() {
    axios.get("/api/posts/" + this.$route.params.id).then((response) => {
      this.post = response.data;
    });
  },
  methods: {
    destroyPost: function(post) {
      axios.delete("/api/posts/" + post.id).then((response) => {
        this.$router.push("/posts");
      });
    }
  }
};
</script>
