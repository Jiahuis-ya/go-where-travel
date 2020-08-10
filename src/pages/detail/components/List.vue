<template>
  <div>
    <!-- <div class="list-item" 
         v-for='(item, index) of list' 
         :key="index">
      <div class="list-item-title border-bottom">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <div v-if="item.children" class="item-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div> -->
    <div class="list-item"
          v-for="(item,index) of categoryList" 
          :key="index">

      <div class="list-item-title border-bottom">
        <span class="item-title-icon"></span>
        {{item.title}}
      </div>
      <!-- <div v-if="item.children" class="item-children" v-for="(i,index) of item.children" :key="index">
        {{i.title}}
      </div> -->
      <div v-if="item.children" class="item-children">
        <detail-list :categoryList="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailList',
  props: {
    list: Array,
    categoryList: Array
  }
}
</script>

<style lang="stylus" scoped>
  .list-item-title{
    width: 100%;
    height: .8rem;
    line-height: .8rem;
    font-size: .32rem;
    text-indent: .6rem;
  }

  .list-item-title .item-title-icon{
    display: inline-block;
    position: absolute;
    width: .36rem;
    height: .36rem;
    top: .26rem;
    left: .2rem;
    background: url(//s.qunarzz.com/piao/image/touch/sight/detail.png) 0 -.45rem no-repeat;
    margin-right: .1rem;
    background-size: .4rem 3rem;
  }

  .item-children{
    padding: 0 .3rem;
  }

  .item-children .list-item-title{
    font-size: .24rem;
  }
</style>
