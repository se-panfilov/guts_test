<template>
  <div class="menu">
    <ul class="menu__container">
      <li class="menu__item">
        <button type="button" @click="onClick()" class="menu-item__button">All</button>
      </li>
      <li class="menu__item" v-for="t in sortedTypes">
        <button type="button" v-text="t" @click="onClick(t)" class="menu-item__button"></button>
      </li>
    </ul>
  </div>
</template>

<script>
  import Games from './games'

  export default {
    name: 'LeftMenu',
    data () {
      return {
        types: []
      }
    },
    mounted () {
      this.types = this.getTypes(Games)
    },
    methods: {
      onClick (val) {
        this.$emit('category-updated', val)
      },
      getTypes (gamesArr) {
        return gamesArr
          .map(v => {
            return v.gameType
          })
          .filter((item, i, arr) => {
            return arr.indexOf(item) === i
          })
      }
    },
    computed: {
      sortedTypes () {
        return this.types.sort((a, b) => {
          if (a.toLowerCase() > b.toLowerCase()) return 1
          if (a.toLowerCase() < b.toLowerCase()) return -1
          return 0
        })
      }
    },
    components: {
      Games
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  .menu
    &__container
      display block
      margin 0
      padding 0

    &__item
        list-style none

    &-item__button
      border 0
      background none
      font-size 0.8em
      cursor pointer
      &:hover, &:active, &:focus
        color red
        outline none


</style>
