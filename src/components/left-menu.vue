<template>
  <div class="left-menu">
    <ul>
      <li v-for="t in types">
      <button type="button" v-text="t"></button>
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
      console.info(this.types)
    },
    methods: {
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
    components: {
      Games
    }
  }
</script>

<style scoped>

</style>
