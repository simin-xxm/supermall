<template>
  <div id="home">
    <nav-bar class="home-nav"></nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <home-recommend-view :recommends="recommends"></home-recommend-view>
  </div>
</template>

<script>

  import NavBar from "../../components/common/navbar/NavBar";
  import HomeSwiper from "./childComps/HomeSwiper";
  import HomeRecommendView from "./childComps/HomeRecommendView";
  import {getHomeMultidata} from "../../network/home";


  export default {
    name: "Home",
    components: {
      NavBar,
      HomeSwiper,
      HomeRecommendView
    },
    data() {
      return {
        //保留下请求的数据
        banners: [],
        recommends: [],
        interval: {
          type: Number,
          default: 1000
        }
      }
    },
    created() {
      //封装请求数据
      getHomeMultidata().then( res => {
        this.banners = res.data.banner;
        this.recommends = res.data.recommend;
      })
    }
  }
</script>

<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color: white;
  }
</style>
