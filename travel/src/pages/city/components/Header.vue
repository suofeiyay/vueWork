<template>
    <div class="header">
        城市选择
        <router-link to='/'>
            <div class="iconfont city-back">&#xe624;</div>
        </router-link>
    </div>
</template>
<script>
export default {
  name: 'CityHeader'
}
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    .header
        position: relative
        height: $HeaderHeight
        line-height: $HeaderHeight
        background: $bgcolor
        color: #fff
        text-align: center
        .city-back
            position: absolute
            top: 0
            left: .3rem
            color: #fff
</style>
