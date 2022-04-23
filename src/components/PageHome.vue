<template>
  <div v-for="thread in threads" :key="thread.id">
    <h2>{{thread.title}}</h2>

    <div v-for="postId in thread.posts" :key="postId">
      <h4>{{findUser(findPost(postId).userId).name}}</h4>
      <p>{{findPost(postId).text}}</p>  
    </div>
  </div>
</template>

<script>
  import sourceData from '@/data.json'
  console.log(sourceData);
  export default {
    data() {
      return {
        threads: sourceData.threads,
        posts: sourceData.posts,
        users: sourceData.users
      }
    },
    methods: {
      findPost(postId) {
        return this.posts.find((post) => post.id === postId)
      },
      findUser(userId) {
        return this.users.find((user) => user.id === userId)
      }
    }
  }
</script>

<style scoped>

</style>