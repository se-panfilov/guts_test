<template>
  <div id="app">
    <main-header v-on:search-updated="setTextFilter"></main-header>
    <left-menu v-on:category-updated="setTypeFilter"></left-menu>
    <games-list
      :text="text"
      :category="category"
    ></games-list>
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

<style>

</style>
