<template>
  <div id="home">
    <nav-bar class="home-nav">
      <template #center>
        <div class="center">购物街</div>
      </template>
    </nav-bar>

    <home-swiper :banners="banners"></home-swiper>

    <recommend-view :recommends="recommends"></recommend-view>
  </div>
</template>

<script>
import NavBar from "@/components/common/navbar/NavBar"
import HomeSwiper from "./childCpns/HomeSwiper";
import RecommendView from "./childCpns/RecommendView";

import {getHomeMultidata} from "@/network/home"


export default {
  name: "home",
  components:{
    NavBar,
    HomeSwiper,
    RecommendView
  },
  data(){
    return {
      banners:[],
      recommends:[]
    }
  },
  created() {
    getHomeMultidata().then(res=>{
      console.log(res);
      this.banners = res.data.data.banner.list;
      this.recommends = res.data.data.recommend.list;
    })
  }
}
</script>

<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color: #fff;
  }
</style>
