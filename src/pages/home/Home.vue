<template>
  <div>
    <HomeHeader :city = "city"></HomeHeader>
    <HomeSwiper :list = "swiperList"></HomeSwiper>
    <HomeIcons :list = "iconList"></HomeIcons>
    <HomeRecommend :list = "recommendList"></HomeRecommend>
    <HomeWeekend :list = "weekendList"></HomeWeekend>
  </div>
</template>
<style>
</style>
<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcons from  './components/Icons'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
export default {
  name: 'Home',
  components: {
    HomeHeader,
    HomeSwiper,
    HomeIcons,
    HomeRecommend,
    HomeWeekend
  },
  data () {
    return {
      lastCity: '',
      city: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  methods: {
    getHomeInfor () {
      console.log('/api/index.json?city='+this.$store.state.city)
        axios.get('/api/index.json?city='+this.$store.state.city).then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
      console.log(res)
      res = res.data;
      if (res.ret && res.data) {
        this.swiperList = res.data.swiperList;
        this.iconList = res.data.iconList;
        this.recommendList = res.data.recommendList;
        this.weekendList = res.data.weekendList;
      }
    }
  },
  mounted () {
    this.city = this.$store.state.city;
    this.lastCity = this.city;
    this.getHomeInfor()
     console.log('mounted')
  },
  activated() {
    if (this.lastCity !== this.city){
      this.lastCity = this.city
      this.getHomeInfor()
    }
    console.log('activated')
  }

}
</script>
