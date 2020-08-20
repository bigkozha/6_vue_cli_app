<template>
  <div id="app" class="container">
    <PostForm @addPost="addPost"></PostForm>
    <div :key="index" v-for="(post, index) in posts" class="row justify-content-center">
      <div class="col-4">
        <Post :text="post.text"></Post>
      </div>
    </div>
  </div>
</template>

<script>
import Post from "./components/Post.vue";
import PostForm from "./components/PostForm.vue";

export default {
  name: "App",
  components: { Post, PostForm },
  data() {
    return {
      posts: [],
    };
  },
  methods: {
    addPost(post) {
      fetch("http://localhost:8000/api/posts/", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify(post),
      }).then((response) => {
        if (response.status === 201) {
          this.posts.unshift({
            text: post.text,
          });
        }
      });
    },
  },
  created() {
    fetch("http://localhost:8000/api/posts/")
      .then((response) => response.json())
      .then((data) => (this.posts = data));
  },
};
</script>