<template>
  <div>
    <router-link
    tag="div"
    class="header-abs"
    to='/'
    v-show="showAbs"
    ><div class="iconfont header-abs-back">&#xe624;</div></router-link>
    <div
    class="header-fixed"
    v-show="!showAbs"
    :style='opacityStyle'
    >
      详情
      <router-link to='/'>
          <div class="iconfont header-fixed-back">&#xe624;</div>
      </router-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'DetailHeader',
  data () {
    return {
      showAbs: true,
      opacityStyle: {
        opacity: 0
      }
    }
  },
  methods: {
    handleScroll () {
      const top = document.documentElement.scrollTop
      if (top > 60) {
        let opacity = top / 140
        opacity = opacity > 1 ? 1 : opacity
        this.opacityStyle = {opacity}
        this.showAbs = false
      } else {
        this.showAbs = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.handleScroll)
  }
}
</script>

<style lang='stylus' scoped>
  @import '~styles/varibles.styl'
  .header-abs
    position absolute
    left .2rem
    top .2rem
    width .8rem
    height .8rem
    line-height .8rem
    text-align center
    border-radius 50%
    background rgba(0,0,0,.8)
    .header-abs-back
      color #fff
      font-size .4rem
  .header-fixed
    position: fixed
    top 0
    left 0
    right 0
    height: $HeaderHeight
    line-height: $HeaderHeight
    background: $bgcolor
    color: #fff
    text-align: center
    z-index 2
    .header-fixed-back
      position: absolute
      top: 0
      left: .3rem
      color: #fff
</style>
