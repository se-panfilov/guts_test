<template>
  <div class='main-list'>
    <ul class='main-list__container'>
      <li v-for='g in filteredGames' class="main-list__item">
        <button @click="toggleGame(g)" class="main-list__btn">
          <img :src='getSrc(g.gameId)' alt='g.name' class="main-list__img">
          <span v-text="g.name" class="main-list__name"></span>
        </button>
      </li>
    </ul>
    <div class="main-game-container"  v-bind:class="{'-active': isGameSelected}">
      <button class="main-game-container__btn" @click="toggleGame()" >X</button>
      <img :src='getSrc(selectedGame)' alt='selectedGame.name' class="main-game-container__img">
    </div>
  </div>
</template>

<script>
  import Games from './games'

  export default {
    name: 'MainHeader',
    data () {
      return {
        games: Games,
        selectedGame: null,
        isGameSelected: false
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
        if (!id) return ''
        return `https://bay1.guts.im/newguts2/images/games/${id}.jpg`
      },
      toggleGame (game) {
        this.selectedGame = (game) ? game.gameId : null
        this.isGameSelected = !this.isGameSelected
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
  text_color = #464646

  .main-list
    color text_color
    position relative
    &__container
      display flex
      flex-direction row
      flex-wrap wrap
      list-style none
      margin 0
      padding 0
    &__item
      color text_color
      padding 3px 5px
    &__btn
      color text_color
      text-decoration none
      border 0
      outline none
      background none
      transition background-color 0.5s ease
      cursor pointer
      &:hover, &:active, &:focus
        background-color #f2f2f2
    &__img
      border-radius 3px
    &__name
      display block
      text-align center

    .main-game-container
      position absolute
      background-color #FFF
      opacity 0
      transition opacity 0.5s ease
      &.-active
        left 0
        right 0
        top 0
        bottom 0
        opacity 1
      &__btn
        display inline-block
        position absolute
        right 0
        border 0
        font-size 18px
        padding 15px
        cursor pointer
      &__img
        width 100%
</style>
