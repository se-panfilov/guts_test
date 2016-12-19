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
