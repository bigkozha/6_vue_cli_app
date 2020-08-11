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
import Post from './components/Post.vue';
import PostForm from './components/PostForm.vue';

export default {
  name: 'App',
  components: { Post, PostForm },
  data() {
    return {
      newPost: '',
      posts: [
        {
          text: 'text 1',
        },
        {
          text: 'text 2',
        },
        {
          text: 'text 3',
        },
      ],
    };
  },
  methods: {
    addPost(text) {
      this.posts.unshift({
        text: text,
      });
    },
  },
};
</script>

<style>
/* #app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
} */
</style>
