<template>
<div>
  <div class="banner" @click="handleBannerClick">
    <img class="banner-image" :src="bannerImage" />
    <div class="banner-info">
      <div class="banner-number">
        <span class="iconfont picture-icon">&#xe622;</span>
        {{this.galleryImages.length}}
      </div>
      <div class="banner-title">{{this.sightName}}</div>
    </div>
  </div>
    <common-fade>
      <common-gallery :imgs-list="galleryImages" 
                    v-show="isGalleryShow"
                    @closeGallery="handleGalleryClose"
                    >
      </common-gallery>
    </common-fade>
</div>
  
</template>

<script>
import CommonGallery from 'common/gallery/Gallery'
import CommonFade from 'common/fade/Fade'
export default{
    name: 'DetailBanner',
    components: {
      'common-gallery': CommonGallery,
      'common-fade': CommonFade
    },
    props: {
      sightName: String,
      bannerImage: String,
      galleryImages: Array
    },
    data: function () {
      return {
        isGalleryShow: false,
       }
    },
    methods: {
      handleBannerClick: function () {
        this.isGalleryShow = true
      },
      handleGalleryClose: function () {
        this.isGalleryShow = false
      }
    }
}
</script>

<style lang="stylus" scoped>

  .banner{
    position: relative;
    overflow: hidden;
    width: 100%;
    height: 0;
    padding-bottom: 55%;
    background-color: #eee;
  }

  .banner .banner-image{
    width: 100%;
  }

  .banner .banner-info{
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    line-height: .6rem;
    color: #fff;
    padding: 0 .2rem .2rem;
    background: linear-gradient(to bottom, rgba(0, 0, 0, 0), rgba(0, 0, 0, 0.6));
  }

  .banner .banner-info .banner-number{
    width: 1.2rem;
    height: .4rem;
    line-height: .4rem;
    text-align: center;
    background: rgba(0, 0, 0, 0.5);
    border-radius: .2rem;
    font-size: .24rem;
  }

  .banner .banner-number .picture-icon{
    font-size: .25rem;
  }

  .banner .banner-info .banner-title{
    width: 100%;
    height: .6rem;
    line-height: .6rem;
    font-size: .36rem;
  }
</style>
