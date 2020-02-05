<template>
  <div class="container mt-10">
    <h2>USERS</h2>

    <ul>
      <li v-for="user in users" :key="user.id">
        <nuxt-link :to="{ name: 'users-id', params: { id: user.id } }">
          {{ user.name }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: []
    }
  },
  async asyncData({ $axios }) {
    const { data } = await $axios.get('/users')

    return {
      users: [...data]
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
