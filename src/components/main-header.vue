<template>
  <div class="header">
    <h1 class="header__title">Guts</h1>
    <ul class="header__menu">
      <li class="header-menu__item">
        <input type="search"
               class="header-menu__input"
               v-model="search"
               @input="updateSearch"
               placeholder="Search"
        />
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'MainHeader',
    data () {
      return {
        search: ''
      }
    },
    methods: {
      updateSearch () {
        this.$emit('search-updated', this.search)
      }
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus" scoped>
  .header
    background-color #F7F7F7
    &__title
      margin 0
      padding 5px 25px
      display inline-block
      width 120px
      text-align center
    &__menu
      display inline-block
      vertical-align super
      list-style none
      margin 0
      padding 5px

  .header-menu
    &__input
      height 34px
      padding 6px 12px
      font-size 14px
      line-height 1.42857143
      border-radius 4px
      border 1px solid #ccc
      font-weight 300
</style>
