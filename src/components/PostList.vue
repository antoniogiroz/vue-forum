<template>
  <div class="post-list">
    <PostListItem
      v-for="post in posts"
      :key="post['.key']"
      :post="post"
    />
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
