<template lang="pug">
  .Wrapper
    .MainBackground
    NavPanel
    LinkContainer
</template>

<script>
  import NavPanel from '@/components/NavPanel'
  import LinkContainer from '@/components/LinkContainer'

  export default {
    components: {
      NavPanel,
      LinkContainer
    },
    beforeMount () {
      const url = localStorage.getItem(this.$route.params.id)
      if (url) {
        window.location.href = localStorage.getItem(this.$route.params.id)
      }
    }
  }
</script>

<style lang="stylus">
  .Wrapper
    position: absolute
    background: #404040
    min-height: 100vh
    min-width: 100vw
    z-index: -2
  .MainBackground
    position: absolute
    background: url('../assets/workspace_on_table_white.jpg')
    min-height: 100vh
    min-width: 100vw
    background-size: cover
    background-position: center
    opacity: .2
    z-index: -1
</style>
