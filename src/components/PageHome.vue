<template>
  Hello from page home
  <div v-for="thread in threads" :key="thread.id">
      <h2>{{thread.title}}</h2>
      <div v-for="postId in thread.posts" :key="postId">
          <p>{{userById(postById(postId).userId).name}}</p>
          <p>{{postById(postId).text}}</p>
      </div>
  </div>
</template>

<script>
import { threads, posts, users } from '@/data.json'

export default {
  data () {
    return {
      threads,
      posts,
      users
    }
  },
  methods: {
    postById (postId) {
      return this.posts.find(p => p.id === postId)
    },
    userById (userId) {
      return this.users.find(p => p.id === userId)
    }
  }
}
</script>

<style>

</style>
