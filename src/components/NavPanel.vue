<template lang="pug">
  .NavPanel
    .NavPanel-link.NavPanel-link--desktop Link 1
    .NavPanel-link.NavPanel-link--desktop Link 2
    .NavPanel-link.NavPanel-link--desktop Link 3
    .NavPanel-link.NavPanel-link--mobile
      i.fa.fa-users
    .NavPanel-link.NavPanel-link--mobile
      i.fa.fa-btc
    .NavPanel-link.NavPanel-link--mobile
      i.fa.fa-apple
    .NavPanel-link.NavPanel-link--sing Sign up
</template>

<script>
  export default {
  }
</script>

<style lang="stylus">
  .NavPanel
    padding: 20px
    display: grid
    grid-template-columns: repeat(3, auto) 1fr
    grid-gap: 20px
  .NavPanel-link
    color: #fff
    padding: 0 30px
    cursor: pointer
    transition: color .3s
    &:hover
      color: #999
    &--desktop
      @media(max-width: 550px)
        display: none
        padding: 0 !important
    &--mobile
      padding: 0
      @media(min-width: 551px)
        display: none
    &--sing
      color: #fff
      text-align: right
      font-weight: 600
</style>
