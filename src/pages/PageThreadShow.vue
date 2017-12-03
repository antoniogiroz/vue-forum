<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <post-list :posts="posts"></post-list>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import PostList from '@/components/PostList'

  export default {
    props: {
      id: {
        required: true,
        type: String
      }
    },

    components: {
      PostList
    },

    data () {
      return {
        thread: sourceData.threads[this.id]
      }
    },

    computed: {
      posts () {
        const postIds = Object.keys(this.thread.posts)
        return Object.values(sourceData.posts)
          .filter(post => postIds.includes(post['.key']))
      }
    }
  }
</script>
