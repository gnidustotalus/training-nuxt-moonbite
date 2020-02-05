<template>
  <div class="container">
    <div>{{ post.title }}</div>
    <div>{{ post.body }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      post: null
    }
  },
  async asyncData({ $axios, params }) {
    const { id } = params

    const { data } = await $axios.get(`/posts/${id}`)

    return {
      post: data
    }
  }
}
</script>

<style></style>
