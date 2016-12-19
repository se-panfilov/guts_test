<template>
  <div class='main-list'>
    <ul class='main-list__container'>
      <li v-for='g in filteredGames' class="main-list__item">
        <img :src='getSrc(g.gameId)' alt='g.name' class="main-list__img">
        <!--<span v-text="g.name" class="main-list__name"></span>-->
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
        return this.games
          .filter(v => {
            if (!this.category) return true
            return v.gameType === this.category
          })
          .filter(v => {
            if (!this.text && this.text.length === 0) return true
            return v.name.toLowerCase().indexOf(this.text.toLowerCase()) !== -1
          })
      }
    },
    components: {
      Games
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  .main-list
    &__container
      display flex
      flex-direction row
      flex-wrap wrap
      list-style none
      margin 0
      padding 0
    &__item
      padding 3px 5px
      /*display block*/
      /*float left*/
    &__img
      border-radius 3px
    &__name
      display block
      color red
      text-align center
</style>
