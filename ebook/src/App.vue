<template>
  <div id="app">
    <ul>
      <li class="txt">1</li>
    </ul>
    <router-view/>
  </div>
</template>

<script>
export default {}
document.addEventListener('DOMContentLoaded', () => {
  const html = document.querySelector('html')
  let fontSize = window.innerWidth / 10
  fontSize = fontSize > 50 ? 50 : fontSize
  html.style.fontSize = fontSize + 'px'
})
</script>
<style lang="scss" scoped>
  @import "./assets/styles/global";

  .txt{
    font-size: px2rem(20)
  }

</style>
