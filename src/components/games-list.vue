<template>
  <div class='main-list'>
    <ul class='main-list__container'>
      <li v-for='g in filteredGames'>
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
    props: {
      text: {
        type: String
      },
      category: {
        type: String
      }
    },
    methods: {
      getSrc (id) {
        return `https://bay1.guts.im/newguts2/images/games/${id}.jpg`
      }
    },
    computed: {
      filteredGames () {
        return this.games // TODO (S.Panfilov)take care of empty fields
          .filter(v => v.gameType === this.category)
          .filter(v => v.name.toLowerCase().indexOf(this.text.toLowerCase()) !== -1)
      }
    },
    components: {
      Games
    }
  }
</script>

<style scoped>

</style>
