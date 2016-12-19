<template>
  <div class="header">
    <h1 class="header__title">Guts</h1>
    <ul class="header__menu--left">
      <li>
        <input type="search"
               v-model="search"
               @input="updateSearch"
        />
      </li>
    </ul>
    <!--<ul class="header__menu&#45;&#45;right header-menu">-->
    <!--<li>-->
    <!--<button type="button" class="header-menu__button">Most popular</button>-->
    <!--</li>-->
    <!--</ul>-->
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

<style scoped>

</style>
