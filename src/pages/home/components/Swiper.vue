<template>
    <div class="sw-wrapper">
        <swiper :options="swiperOption" v-if="swiperShow">
            <!-- slides -->
            <swiper-slide v-for="item of swiperList" :key="item.id">
                <img class="swiper-img" :src="item.imgUrl" />
            </swiper-slide>
            <!-- Optional controls -->
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>

<script>
export default{
    name: 'HomeSwiper',
    props: {
      swiperList: Array
    },
    data: function () {
        return {
          swiperOption: {
            pagination: {
                el: '.swiper-pagination',
            },
            loop: true
          }
        }
    },
    computed: {
      swiperShow: function () {
        return this.swiperList.length
      }
    }
}
</script>

<style lang="stylus" scoped>
    .sw-wrapper >>> .swiper-pagination-bullet-active{
        background-color: #fff !important;
    }

    .sw-wrapper{
        overflow: hidden;
        width: 100%;
        height: 2.04rem;
        background-color: #eee;
    }

    .swiper-img{
        width: 100%;
        height: 2.04rem;
    }
</style>
