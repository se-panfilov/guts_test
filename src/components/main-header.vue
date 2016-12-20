<template>
  <div class="header">
    <h1 class="header__title">Guts</h1>
    <ul class="header__menu">
      <li class="header-menu__item">
        <input type="search"
               class="header-menu__input"
               v-model="search"
               @input="updateSearch"
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
    &__title
      margin 0
      padding 0 25px
      display inline-block
    &__menu
      display inline-block
      list-style none
      margin 0
      padding 0

  /*.header-menu*/
    /*&__input*/
      /*padding 15px*/

</style>
