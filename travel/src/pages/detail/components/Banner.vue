<template>
  <div>
    <div class="banner" @click="handleBannerClick">
      <img class="banner-img" src="http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_600x330_93d96bdf.jpg" alt="">
      <div class="banner-info">
        <div class="banner-title">
          大连亚圣海洋世界（AAAAA景区）
        </div>
        <div class="banner-number">
          <span class="iconfont banner-icon">&#xe692;</span>39
        </div>
      </div>
    </div>
    <common-gallary
    :imgs='imgs'
    v-show='showGallary'
    @close='handleBannerClose'
    ></common-gallary>
  </div>
</template>
<script>
import CommonGallary from 'common/gallary/Gallary'
export default {
  name: 'DetailBanner',
  data () {
    return {
      imgs: ['http://img1.qunarzz.com/sight/p0/1508/89/895a1b7add84f23faca053ce9e3153db.water.jpg_600x330_93d96bdf.jpg'],
      showGallary: false
    }
  },
  methods: {
    handleBannerClick () {
      this.showGallary = true
    },
    handleBannerClose () {
      this.showGallary = false
    }
  },
  components: {
    CommonGallary
  }
}
</script>
<style lang="stylus" scoped>
  .banner
    position relative
    overflow hidden
    height 0
    padding-bottom 55%
    .banner-img
      width 100%
    .banner-info
      display flex
      position absolute
      left 0
      right 0
      // top 0
      bottom 0
      line-height .6rem
      color #fff
      text-shadow 0 1px 2px rgba(0,0,0,0.70)
      background-image linear-gradient(to bottom,rgba(0,0,0,0),rgba(0,0,0,.8));
      .banner-title
        flex 1
        font-size .32rem
        padding 0 .2rem
      .banner-number
        height .4rem
        margin-top .14rem
        padding 0 .4rem
        font-size .24rem
        line-height .4rem
        border-radius .2rem
        background rgba(0,0,0,.8)
        .banner-icon
          font-size .24rem
          vertical-align top
          margin-right .1rem
</style>
