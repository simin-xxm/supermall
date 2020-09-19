<template>
  <div id="home">
    <nav-bar class="home-nav"></nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <home-recommend-view :recommends="recommends"></home-recommend-view>
    <feature-view />
    <tab-control :titles="['流行','新款','精选']" />
  </div>
</template>

<script>

  import NavBar from "../../components/common/navbar/NavBar";
  import HomeSwiper from "./childComps/HomeSwiper";
  import HomeRecommendView from "./childComps/HomeRecommendView";
  import FeatureView from "./childComps/FeatureView";
  import TabControl from "../../components/content/tabControl/TabControl";

  import {getHomeMultidata} from "../../network/home";


  export default {
    name: "Home",
    components: {
      NavBar,
      HomeSwiper,
      HomeRecommendView,
      FeatureView,
      TabControl
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
  #home{
    padding: 44px 0 49px 0 ;
  }
  .home-nav{
    background-color: var(--color-tint);
    color: white;
    position: fixed;
    left: 0;
    top: 0;
    right: 0;
    z-index: 2;
  }
</style>
