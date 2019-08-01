<template>
    <div>
      <detail-banner
      :sightName="sightName"
      :gallaryImgs="gallaryImgs"
      :bannerImg="bannerImg"
      ></detail-banner>
      <detail-header></detail-header>
      <detail-list :list='list'></detail-list>
      <div class="detail-content"></div>
    </div>
</template>
<script>
import DetailBanner from './components/Banner'
import DetailHeader from './components/Header'
import DetailList from './components/List'
import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'Detail',
  components: {
    DetailBanner,
    DetailHeader,
    DetailList
  },
  data () {
    return {
      sightName: '',
      bannerImg: '',
      gallaryImgs: [],
      list: []
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getDetailInfo () {
      axios.get('/detail.json', {
        params: {
          id: this.$route.params.id
        }
      })
        .then(this.getDetailInfoSucc)
    },
    getDetailInfoSucc (res) {
      res = res.data
      if (res.ret && res.data) {
        this.sightName = res.data.sightName
        this.bannerImg = res.data.bannerImg
        this.gallaryImgs = res.data.gallaryImgs
        this.list = res.data.categoryList
      }
    }
  },
  mounted () {
    this.getDetailInfo()
  }
}
</script>
<style lang='stylus' scoped>
  .detail-content
    height 50rem
</style>
