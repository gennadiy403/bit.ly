<template lang="pug">
  .LinkContainer
    input.LinkContainer-input(
      v-model="srcLink"
      @keyup.enter="getShortenLink"
      type="text"
      placeholder="Just past your link here"
    )
    button.LinkContainer-submit(
      @click="getShortenLink"
      @mouseover="changeButtonTextOver"
      @mouseout="changeButtonTextOut"
      :disabled="!srcLink"
    ) {{ buttonText }}
    .LinkContainer-encoded(v-if="encodedLink") OK, this is your shorten link:
      .LinkContainer-link {{ hostname }}/{{ encodedLink }}
</template>

<script>
  import md5 from 'md5'

  export default {
    data () {
      return {
        srcLink: null,
        encodedLink: null,
        buttonText: 'Let it bit.ly'
      }
    },
    computed: {
      hostname () {
        return location.hostname + (location.port ? ':' + location.port : '')
      }
    },
    methods: {
      changeButtonTextOver () {
        this.buttonText = 'Let it bit.lz'
      },
      changeButtonTextOut () {
        this.buttonText = 'Let it bit.ly'
      },
      getShortenLink () {
        this.encode(this.srcLink)
      },
      encode (link) {
        if (!link.match(/^http/)) {
          link = `http://${link}`
        }
        let key = md5(link).slice(0, 5)
        localStorage.setItem(key, link)
        this.encodedLink = key
      }
    }
  }
</script>

<style lang="stylus">
  .LinkContainer
    margin-top: 30vh
    height: 30px
    display: grid
    grid-template-columns: minmax(100px, 800px) auto
    grid-gap: 10px
    padding: 0 50px
    justify-content: center
    &-input
      padding: 10px 20px
    &-submit
      font-weight: 500
      white-space: nowrap
      transition: all 1s
      cursor: pointer
    &-encoded
      grid-column: 1 / 3
      color: #fff
    &-link
      font-weight: 800
</style>
