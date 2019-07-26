<template>
    <div>
      <detail-banner></detail-banner>
    </div>
</template>
<script>
import DetailBanner from './components/Banner'
// import axios from 'axios'
import { mapState } from 'vuex'
export default {
  name: 'Detail',
  components: {
    DetailBanner
  },
  data () {
    return {
    }
  },
  computed: {
    ...mapState(['city'])
  },
  methods: {
    getHomeInfo () {
      // axios.get()
      //   .then(this.getHomeInfoSucc)
    },
    getHomeInfoSucc (res) {
    }
  }
}
</script>
<style lang="">
</style>
