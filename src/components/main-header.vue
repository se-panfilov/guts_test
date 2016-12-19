<template>
  <div class="header">
    <h1 class="header__title">Guts</h1>
    <ul class="header__menu--left">
      <li>
        <input type="search"
               v-model="search"
        />
      </li>
    </ul>
    <ul class="header__menu--right header-menu">
      <li>
        <button type="button" class="header-menu__button">Most popular</button>
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
    }
  }
</script>

<style scoped>

</style>
