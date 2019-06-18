<template>
  <div class="wraper">
    <swiper :options="swiperOption" ref="mySwiper">
      <!-- slides -->
      <swiper-slide v-for="item of swiperList" :key="item.key">
        <img class="swiper-img" :src="item.imgUrl" alt>
      </swiper-slide>
      <div class="swiper-pagination" slot="pagination"></div>
    </swiper>
  </div>
</template>

<script>
export default {
  name: 'HomeSwiper',
  data () {
    return {
      swiperOption: {
        pagination: '.swiper-pagination',
        loop: true
      },
      swiperList: [
        {
          id: 'img1',
          imgUrl:
            'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20196/e440c31af79c0b9d1a1e84c577205562.jpg_750x200_0729c45b.jpg'
        },
        {
          id: 'img2',
          imgUrl:
            'http://mp-piao-admincp.qunarzz.com/mp_piao_admin_mp_piao_admin/admin/20195/aef5f8864f5a1167599609307571b2c4.jpg_750x200_db7bedbe.jpg'
        }
      ]
    }
  },
  computed: {
    swiper () {
      return this.$refs.mySwiper.swiper
    }
  },
  mounted () {
    this.swiper.slideTo(3, 1000, false)
  }
}
</script>
<style lang="stylus" scoped>
.wraper >>> .swiper-pagination-bullet-active { // 样式穿透
  background: #fff;
}

.wraper {
  overflow: hidden;
  width: 100%;
  height: 0;
  padding-bottom: 26.7%; // 限定宽高比
  background: #eee;

  .swiper-img {
    width: 100%;
  }
}
</style>
