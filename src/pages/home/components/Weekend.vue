<template>
  <div class="recommend-wrapper">
    <div class="recommend-title">
      周末去哪儿
    </div>
    <ul>
      <li class="list-item" v-for="(item, index) of weekendList" :key="index">
        <div class="item-img">
          <img :src="item.imgUrl" />
        </div>
        <div class="item-info">
          <div class="inner-box">
            <div class="info-title">{{item.title}}</div>
            <div class="info-comment">{{item.comment}}</div>
          </div>
        </div>
      </li>
    </ul>
  </div>
  
</template>

<script>
export default{
  name: 'HomeWeekend',
  props: {
    weekendList: Array
  }
}
</script>

<style lang="stylus" scoped>
  @import '~styles/variables.styl'
  @import '~styles/mixins.styl'
  div{
    box-sizing: border-box;
  }

  .recommend-title{
    width: 100%;
    height: .8rem;
    line-height: .8rem;
    font-size: .28rem;
    background-color: #eee;
    padding: 0 .2rem;
  }

  .list-item .item-img{
    overflow: hidden;
    width: 100%;
    height: 0;
    padding-bottom: 37.1%;
    background-color: pink;
  }

  .list-item .item-img img{
    width: 100%;
  }

  .list-item .item-info{
    float: left;
    width: 100%;
    height: 1.24rem;
    padding: .14rem .2rem .2rem .2rem;
  }

  .list-item .item-info .inner-box .info-title{
    width: 100%;
    height: .48rem;
    line-height: .48rem;
    font-size: .28rem;
    ellipsis();
  }

  .list-item .item-info .inner-box .info-comment{
    width: 100%;
    height: .42rem;
    line-height: .42rem;
    font-size: .24rem;
  }

</style>
