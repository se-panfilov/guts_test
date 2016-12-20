<template>
  <div id="app">
    <main-header v-on:search-updated="setTextFilter" class="header"></main-header>
    <div class="row">
      <left-menu v-on:category-updated="setTypeFilter" class="menu"></left-menu>
      <games-list
        :text="text"
        :category="category"
        class="list"
      ></games-list>
    </div>
  </div>
</template>

<script>
  import MainHeader from './components/main-header'
  import LeftMenu from './components/left-menu'
  import GamesList from './components/games-list'

  export default {
    name: 'app',
    data () {
      return {
        text: '',
        category: null
      }
    },
    methods: {
      setTextFilter (val) {
        this.text = val
      },
      setTypeFilter (val) {
        this.category = val
      }
    },
    components: {
      MainHeader,
      LeftMenu,
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
    justify-content center
    padding 0 25px
    .menu
      /*flex-basis 300px*/
      min-width 160px
      flex-grow 1
      flex-shrink 2
    .list
      flex-grow 2
      flex-shrink 1
</style>

<style lang="stylus" rel="stylesheet/stylus">
  html, body
    margin 0
    padding 0
    height 100%

  body
    background-color #F7F7F7
    color main_text_color
    font-family 'Roboto', sans-serif
    font-weight 500
    font-size 16px
    *
      font-family 'Roboto', sans-serif
      font-weight 500

    #app
      padding-left 15px
      padding-right 15px

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
