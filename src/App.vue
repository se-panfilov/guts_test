<template>
  <div id="app">
    <main-header></main-header>
    <games-list></games-list>

  </div>
</template>

<script>
import MainHeader from './components/main-header'
import GamesList from './components/games-list'

export default {
  name: 'app',
  components: {
    MainHeader,
    GamesList
  }
}
</script>

<style>

</style>
