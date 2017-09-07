<template>
  <transition name="slid">
    <div class="singer-detail">
 <<<<<<<<<<<<<<<<<<<<<<<<<<<<
    </div>
  </transition>
</template>

<script type="text/ecmascript-6">
import { getSingerDetail } from 'api/singer'
import { ERR_OK } from 'api/config'
import { mapGetters } from 'vuex'

export default {
  computed: {
    ...mapGetters([
      'singer'
    ])
  },
  created() {
    this._getDetail()
  },
  methods: {
    _getDetail() {
      if (!this.singer.id) {
        this.$router.push('/singer')
        return
      }
      getSingerDetail(this.singer.id).then((res) => {
        if (res.code === ERR_OK) {
          console.log(res.data.list)
        }
      })
    }
  }
}
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
  @import "~common/stylus/variable"

  .singer-detail
    position: fixed
    z-index: 100
    top: 0
    left: 0
    right: 0
    bottom: 0
    background: $color-background

  .slid-enter-active, .slid-leave-active 
    transition: all .3s

  .slid-enter, .slid-leave-to
    transform: translate3d(100%,0,0)

</style>
