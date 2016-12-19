<template>
  <div id="app">
    <main-header></main-header>

  </div>
</template>

<script>
import MainHeader from './components/main-header.vue'

export default {
  name: 'app',
  components: {
    MainHeader
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
