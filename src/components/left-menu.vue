<template>
  <div class="left-menu">
    <ul>
      <li>
        <button type="button" @click="onClick()">All</button>
      </li>
      <li v-for="t in sortedTypes">
        <button type="button" v-text="t" @click="onClick(t)"></button>
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

<style scoped>

</style>
