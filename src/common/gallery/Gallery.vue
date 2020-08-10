<template>
  <div class="gallery-container" @click="handleGalleryClick">
    <div class="img-wrapper">
      <swiper :options="swiperOption">
        <!-- slides -->
        <swiper-slide v-for="(item, index) of imgsList" :key="index">
            <img class="gallery-img" :src="item" />
        </swiper-slide>
        <!-- Optional controls -->
        <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
  </div>
</template>

<script>
export default{
  name: 'CommonGallery',
  props: {
    imgsList: {
      type: Array,
      default: function () {
        return []
      }
    }
  },
  data: function () {
      return {
        swiperOption: {
            pagination: {
                el: '.swiper-pagination',
                type: 'fraction'
            },
            observer: true,
            observeParents: true
        }
      }
  },
  methods: {
    handleGalleryClick: function () {
      this.$emit('closeGallery')
    }
  }
}
</script>

<style lang="stylus" scoped>
  div{
      display: flex;
  }

  .gallery-container >>> .swiper-container{
    overflow: visible;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }

  .gallery-container{
    flex-direction: column;
    justify-content: center;
    position: fixed;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    background-color: #000;
    z-index: 1;
  }

  .gallery-container .img-wrapper{
    position: relative;
    width: 100%;
    height: 0;
    padding-bottom: 70%;
    color: #fff;
  }

  .gallery-container .img-wrapper .gallery-img{
    width: 100%;
  }

  .gallery-container .img-wrapper .swiper-pagination{
    bottom: -1rem;
    justify-content: center;
  }
</style>
