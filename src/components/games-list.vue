<template>
  <div class='main-list'>
    <ul class='main-list__container'>
      <li v-for='g in games'>
        <img :src='getSrc(g.gameId)' alt='g.name'>
        <span v-text="g.name"></span>
      </li>
    </ul>
  </div>
</template>

<script>
  import Games from './games'

  export default {
    name: 'MainHeader',
    data () {
      return {
        games: Games
      }
    },
//    mounted () {
//      this.games = this.getTypes(Games)
//      console.info(this.types)
//    },
    methods: {
      getSrc (id) {
        return `https://bay1.guts.im/newguts2/images/games/${id}.jpg`
      }
    },
    components: {
      Games
    }
  }
</script>

<style scoped>

</style>
