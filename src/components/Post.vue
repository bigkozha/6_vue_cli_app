<template>
  <b-card size="m-2">
    <div class="card-body">{{text}}</div>
  </b-card>
</template>

<script>
export default {
  name: 'Post',
  props: ['text'],
  data() {
    return {};
  },
};
</script>