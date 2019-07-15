<template>
  <div>
     <div class="search">
      <input v-model='keyword' class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
    <div class="search-content" ref='search' v-show='keyword'>
      <ul>
        <li class="search-item" v-for="item of list" :key='item.id'>{{item.name}}</li>
        <li class="search-item search-item-bottom" v-show="hasNodata">没有找到匹配数据</li>
      </ul>
    </div>
  </div>
</template>
<script>
import { clearTimeout, setTimeout } from 'timers'
import BScroll from 'better-scroll'
export default {
  name: 'CitySearch',
  props: {
    cities: Object
  },
  data () {
    return {
      keyword: '',
      list: [],
      timer: null
    }
  },
  mounted () {
    this.scroll = new BScroll(this.$refs.search)
  },
  computed: {
    hasNodata () {
      return !this.list.length
    }
  },
  watch: {
    keyword () {
      if (this.timer) {
        clearTimeout(this.timer)
      }
      if (!this.keyword) {
        this.list = []
        return
      }
      this.timer = setTimeout(() => {
        const result = []
        for (let i in this.cities) {
          this.cities[i].forEach((value) => {
            if (value.spell.indexOf(this.keyword) > -1 || value.name.indexOf(this.keyword) > -1) {
              result.push(value)
            }
          })
        }
        this.list = result
      }, 100)
    }
  }
}
</script>
<style lang="stylus" scoped>
  @import '~styles/varibles'
  .search
    height .72rem
    background $bgcolor
    padding 0 .1rem
    .search-input
      box-sizing border-box
      height .62rem
      width 100%
      color #333
      line-height .62rem
      text-align center
      border-radius .06rem
      padding 0 .1rem
  .search-content
    position absolute
    top 1.58rem
    left 0
    right 0
    bottom 0
    overflow hidden
    background #eee
    z-index 1
    .search-item
      line-height .62rem
      padding-left 0.8rem
      color #333
      background #ffffff
      border-bottom 1px solid #eee
</style>
