<template>
  <Swiper>
    <swiper-item v-for="item in banners.list">
      <a :href="item.link">
        <img :src="item.image" alt="">
      </a>
    </swiper-item>
  </Swiper>
</template>

<script>
  import {Swiper, SwiperItem} from '../../../components/common/swiper'

  export default {
    name: "HomeSwiper",
    components: {
      Swiper,
      SwiperItem
    },
    props: {
      banners: {
        type: Array,
        default() {
          return [];
        }
      }
    }
  }
</script>

<style scoped>

</style>
