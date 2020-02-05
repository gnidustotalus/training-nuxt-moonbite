<template>
  <div v-swiper:mySwiper="swiperOption" class="my-swiper">
    <div class="swiper-wrapper">
      <div v-for="slide in users" :key="slide.id" class="swiper-slide">
        {{ slide.name }}
      </div>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Vue from 'vue'

if (process.browser) {
  require('swiper/dist/css/swiper.css')
  const VueAwesomeSwiper = require('vue-awesome-swiper/dist/ssr')
  Vue.use(VueAwesomeSwiper)
}

export default {
  data() {
    return {
      users: null,
      swiperOption: {
        pagination: {
          el: '.swiper-pagination'
        }
      }
    }
  },
  async asyncData({ $axios }) {
    const { data } = await $axios.get('/users')

    return {
      users: data
    }
  }
}
</script>

<style>
.my-swiper {
  height: 300px;
  width: 100%;
}
.swiper-slide {
  text-align: center;
  font-size: 38px;
  font-weight: 700;
  background-color: #eee;
  display: flex;
  justify-content: center;
  align-items: center;
}
.swiper-pagination > .swiper-pagination-bullet {
  background-color: red;
}
</style>
