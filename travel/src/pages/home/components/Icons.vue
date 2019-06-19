<template>
    <div class="icons">
        <swiper :options="swiperOption" ref="mySwiper">
            <swiper-slide  v-for="page of pages" :key="page.index">
               <div class="icon" v-for="item of page" :key="item.key">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.desc}}</p>
                </div>
            </swiper-slide>
            <div class="swiper-pagination" slot="pagination"></div>
        </swiper>
    </div>
</template>
<script>
export default {
  name: 'HomeIcons',
  props: {
    list: Array
  },
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        autoplay: false
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.list.forEach((item, index) => {
        const page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(item)
      })
      return pages
    }
  }
}
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    @import '~styles/mixins.styl'
    .icons
        overflow: hidden
        height: 0
        padding-bottom: 50%
        margin: .2rem 0
        .icon
            position: relative
            float: left
            width: 25%
            height: 0
            overflow: hidden
            padding-bottom: 25%
            .icon-img
                position: absolute
                top:0
                left: 0
                right: 0
                bottom: .44rem
                .icon-img-content
                    display: block
                    height: 100%
                    margin: 0 auto
            .icon-desc
                position: absolute
                left: 0
                right: 0
                bottom: 0
                height: .44rem
                line-height: .44rem
                text-align: center
                color: $DarkTextColor
                font-size: .24rem
                ellipsis()
</style>
