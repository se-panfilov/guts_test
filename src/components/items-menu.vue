<template>
  <div class="menu">
    <ul class="menu__container">
      <li class="menu__item">
        <button type="button" @click="onClick()" class="menu-item__button">All</button>
      </li>
      <li class="menu__item" v-for="t in sortedItems">
        <button type="button" v-text="t" @click="onClick(t)" class="menu-item__button"></button>
      </li>
    </ul>
  </div>
</template>

<script>
  import Games from './games'

  export default {
    name: 'ItemsMenu',
    data () {
      return {
        items: []
      }
    },
    props: {
      fieldName: {
        type: String
      }
    },
    mounted () {
      this.items = this.getItems(Games)
    },
    methods: {
      onClick (val) {
        this.$emit('items-updated', val)
      },
      getItems (gamesArr) {
        return gamesArr
          .map(v => {
            return v[this.fieldName]
          })
          .filter((item, i, arr) => {
            return arr.indexOf(item) === i
          })
      }
    },
    computed: {
      sortedItems () {
        return this.items.sort((a, b) => {
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
  text_color = #464646
  bg_color = #FFF

  .menu
    &__container
      display block
      margin 0
      padding 0 15px
      height 100%

    &__item
        list-style none

    &-item__button
      border 0
      background none
      font-size 0.8em
      cursor pointer
      color text_color
      font-weight 300
      width 100%
      text-align left
      background-color bg_color
      transition background-color 0.3s ease
      &:hover, &:active, &:focus
        color black
        outline none
        background-color darken(bg_color, 5)


</style>
