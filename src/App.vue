<template>
  <div id="app">
    <main-header></main-header>
    <left-menu></left-menu>
    <games-list></games-list>
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
