<template>
  <div id="app">
    <main-header v-on:search-updated="setTextFilter" class="header"></main-header>
    <transition name="in-out-translate-fade" mode="out-in" appear>
      <div class="row">
        <div class="menu">
          <h4>Category</h4>
          <items-menu
            v-on:items-updated="setCategoryFilter"
            field-name="gameType"
          ></items-menu>
          <h4>Vendor</h4>
          <items-menu
            v-on:items-updated="setVendorFilter"
            field-name="vendor"
          ></items-menu>
        </div>
        <games-list
          :text="text"
          :category="category"
          :vendor="vendor"
          class="list"
        ></games-list>
      </div>
    </transition>
  </div>
</template>

<script>
  import MainHeader from './components/main-header'
  import ItemsMenu from './components/items-menu'
  import GamesList from './components/games-list'

  export default {
    name: 'app',
    data () {
      return {
        text: '',
        category: null,
        vendor: null
      }
    },
    methods: {
      setTextFilter (val) {
        this.text = val
      },
      setCategoryFilter (val) {
        this.category = val
      },
      setVendorFilter (val) {
        this.vendor = val
      }
    },
    components: {
      MainHeader,
      ItemsMenu,
      GamesList
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  .header
    display block

  .row
    display flex
    flex-direction row
    flex-wrap nowrap
    justify-content space-around
    padding 15px
    background #FFF
    .menu
      flex 0 0 150px
    .list
      flex-grow 2
      flex-shrink 1

  .in-out-translate-fade-enter-active, .in-out-translate-fade-leave-active
    transition all 0.5s

  .in-out-translate-fade-enter, .in-out-translate-fade-leave-active
    opacity 0

  .in-out-translate-fade-enter
    transform translateX(31px)

  .in-out-translate-fade-leave-active
    transform translateX(-31px)

</style>

<style lang="stylus" rel="stylesheet/stylus">
  html, body
    margin 0
    padding 0
    height 100%

  body
    background-color #FFF
    color #3c3c3c
    font-family 'Roboto', sans-serif
    font-weight 500
    font-size 16px
    *
      font-family 'Roboto', sans-serif
      font-weight 500

  //#app
  //padding-left 15px
  //padding-right 15px

  input[type="search"]
    -moz-appearance textfield
    -webkit-appearance textfield
    appearance textfield
    -webkit-box-sizing border-box
    -moz-box-sizing border-box
    box-sizing border-box

  article, aside, details, figcaption, figure,
  footer, header, menu, nav, section, canvas
    display block

</style>
