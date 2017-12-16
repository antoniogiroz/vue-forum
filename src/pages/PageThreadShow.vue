<template>
  <div class="col-large push-top">
    <h1>{{thread.title}}</h1>
    <post-list :posts="posts"></post-list>
    <post-editor
      :threadId="id"
      @save="addPost"
    ></post-editor>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import PostList from '@/components/PostList'
  import PostEditor from '@/components/PostEditor'

  export default {
    props: {
      id: {
        required: true,
        type: String
      }
    },

    components: {
      PostList,
      PostEditor
    },

    data () {
      return {
        thread: sourceData.threads[this.id],
        newPostText: ''
      }
    },

    computed: {
      posts () {
        const postIds = Object.keys(this.thread.posts)
        return Object.values(sourceData.posts)
          .filter(post => postIds.includes(post['.key']))
      }
    },

    methods: {
      addPost (eventData) {
        const post = eventData.post
        const postId = post['.key']
        this.$set(sourceData.posts, postId, post)
        this.$set(this.thread.posts, postId, postId)
        this.$set(sourceData.users[post.userId].posts, postId, postId)
      }
    }
  }
</script>
