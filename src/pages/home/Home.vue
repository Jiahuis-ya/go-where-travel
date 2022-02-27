<template>
<div>
    <home-header></home-header>
    <home-swiper :swiper-list="swiperList"></home-swiper>
    <home-icon :icon-list="iconList"></home-icon>
    <home-recommend :recommend-list="recommendList"></home-recommend>
    <home-weekend :weekend-list="weekendList"></home-weekend>
</div>

</template>

<script>
import HomeHeader from './components/Header'
import HomeSwiper from './components/Swiper'
import HomeIcon from './components/Icon'
import HomeRecommend from './components/Recommend'
import HomeWeekend from './components/Weekend'
import axios from 'axios'
import { mapState } from 'vuex'
export default{
  name: 'Home',
  components: {
    // HomeHeader: HomeHeader或
    'home-header': HomeHeader,
    'home-swiper': HomeSwiper,
    'home-icon': HomeIcon,
    'home-recommend': HomeRecommend,
    'home-weekend': HomeWeekend
  },
  computed: {
    ...mapState({
      curCity: 'city'
    })
  },
  data: function () {
    return {
      lastCity: '',
      swiperList: [],
      iconList: [],
      recommendList: [],
      weekendList: []
    }
  },
  methods: {
    getHomeInfo: function () {
      axios.get('/travel-h5-page/api/index.json?city=' + this.curCity)
        .then(this.getHomeInfoSuccess)
    },
    getHomeInfoSuccess: function (res) {
      if (res.data.ret && res.data.data) {
        var data = res.data.data
        this.swiperList = data.swiperList
        this.iconList = data.iconList
        this.recommendList = data.recommendList
        this.weekendList = data.weekendList
      }
    }
  },
  mounted: function () {
    this.lastCity = this.curCity
    this.getHomeInfo()
  },
  activated: function () {
    if (this.lastCity !== this.curCity) {
      this.lastCity = this.curCity
      this.getHomeInfo()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
