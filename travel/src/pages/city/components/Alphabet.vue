<template>
  <ul class="list">
   <li class="item">A</li>
   <li class="item">B</li>
   <li class="item">C</li>
   <li class="item">D</li>
  </ul>
</template>
<script>
export default {
  name: 'CityAlphabet'
}
</script>
<style lang="stylus" scoped>
   @import '~styles/varibles'
   .list
    display flex
    flex-direction column
    justify-content center
    position absolute
    right 0
    top 1.58rem
    bottom 0
    width .4rem
    color red
    .item
      text-align center
      line-height .44rem
      color $bgcolor
</style>
