<template>
  <div class="post-list">
    <post-list-item
      v-for="post in posts"
      :key="post['.key']"
      :post="post"
    ></post-list-item>
  </div>
</template>

<script>
  import PostListItem from './PostListItem'

  export default {
    name: 'post-list',

    components: {
      PostListItem
    },

    props: {
      posts: {
        required: true,
        type: Array
      }
    }
  }
</script>

<style scoped>

</style>
