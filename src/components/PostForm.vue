<template>
  <div class="row justify-content-center mt-3">
    <div class="jumbotron">
      <div class="container">
        <h4>Posting a text</h4>
        <div class="input-group mb-3">
          <input
          id="id_text"
            v-model="post.text"
            type="text"
            class="form-control"
            placeholder="ur text"
            aria-label="ur text"
            aria-describedby="button-addon2"
          />
          <div class="input-group-append">
            <button
              v-on:click="addPost"
              class="btn btn-outline-secondary"
              type="button"
              id="button-addon2"
            >Post</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'PostForm',
  data() {
    return {
      post: {},
    };
  },
  methods: {
    addPost() {
      this.post.created_at = new Date();
      this.$emit('addPost', this.post);
    },
  },
};
</script>