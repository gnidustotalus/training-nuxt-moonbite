<template>
  <div class="container">
    <div>{{ user.name }}</div>
    <div>{{ user.email }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: null
    }
  },
  async asyncData({ $axios, params }) {
    const { id } = params
    console.log(id, 'ID')

    const { data } = await $axios.get(`/users/${id}`)

    return {
      user: data
    }
  }
}
</script>

<style></style>
