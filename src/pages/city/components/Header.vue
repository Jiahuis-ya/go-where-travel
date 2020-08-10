<template>
  <div class="header">
    <router-link to="/">
    <span class="iconfont city-hd-back-icon">&#xe6a0;</span>
    </router-link>
    城市选择
  </div>
</template>

<script>
export default {
  name: 'CityHeader'
}
</script>

<style lang="stylus" scoped>
  @import '~styles/variables.styl'
  .header{
    position: relative;
    width: 100%;
    height: $headerHt;
    line-height: $headerHt;
    text-align: center;
    color: #fff;
    font-size: .32rem;
    background-color: $bgColor;
  }

  .header .city-hd-back-icon{
    position: absolute;
    top: 0;
    left: .2rem;
    color: #fff;
  }
</style>
