<template>
  <div class="col-full">
    <h1>Welcome to the Forum</h1>
    <thread-list :threads="threads"></thread-list>
  </div>
</template>

<script>
  import sourceData from '@/data'
  import ThreadList from './ThreadList'
  console.log(sourceData)

  export default {
    name: 'HelloWorld',

    components: {
      ThreadList
    },

    data () {
      return {
        threads: Object.values(sourceData.threads),
        posts: sourceData.posts,
        users: sourceData.users
      }
    }
  }
</script>
