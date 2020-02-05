<template>
  <div class="container mt-10">
    <h2>POSTS</h2>

    <ul>
      <li v-for="post in posts" :key="post.id">
        <nuxt-link :to="{ name: 'posts-id', params: { id: post.id } }">
          {{ post.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      posts: []
    }
  },
  async asyncData({ $axios }) {
    const { data } = await $axios.get('/posts')

    return {
      posts: [...data]
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 1920px;
  padding-left: 15px;
  padding-right: 15px;
  margin: 0 auto;
}

.mt-10 {
  margin-top: 100px;
}
</style>
