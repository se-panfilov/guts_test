<template>
  <div id="app">
    <main-header></main-header>
    <games-list></games-list>
    <left-menu></left-menu>
  </div>
</template>

<script>
import MainHeader from './components/main-header'
import LeftMenu from './components/left-menu'
import GamesList from './components/games-list'

export default {
  name: 'app',
  components: {
    MainHeader,
    LeftMenu,
    GamesList
  }
}
</script>

<style>

</style>
