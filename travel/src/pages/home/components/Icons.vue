<template>
    <div class="icons">
        <swiper :options="swiperOption" ref="mySwiper">
            <swiper-slide  v-for="page of pages" :key="page.index">
               <div class="icon" v-for="item of page" :key="item.key">
                    <div class="icon-img">
                        <img class="icon-img-content" :src="item.imgUrl" alt="">
                    </div>
                    <p class="icon-desc">{{item.text}}</p>
                </div>
            </swiper-slide>
            <!-- <div class="swiper-pagination" slot="pagination"></div> -->
        </swiper>
    </div>
</template>
<script>
export default {
  name: 'HomeIcons',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination'
      },
      iconList: [{
        key: 'icon1',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
        text: '景点门票'
      }, {
        key: 'icon2',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20193/f0f00d6dfe038c044dbc9a437f58b0eb.png',
        text: '一日游'
      }, {
        key: 'icon3',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
        text: '北京必游'
      }, {
        key: 'icon4',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/3e/86314b2af03b7502.png',
        text: '水上乐园'
      }, {
        key: 'icon5',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20191/0334cf5430b9b5505fd79e2b8d7e8670.png',
        text: '爬长城'
      }, {
        key: 'icon6',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png',
        text: '故宫'
      }, {
        key: 'icon7',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
        text: '动植物园'
      }, {
        key: 'icon8',
        imgUrl: 'http://img1.qunarzz.com/piao/fusion/1805/3a/754b47f658e9c602.png',
        text: '怀北漂流'
      }, {
        key: 'icon9',
        imgUrl: 'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20194/b4511345827006994aa1980a3886f0ac.png',
        text: '北京世园会'
      }]
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconList.forEach((item, index) => {
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
