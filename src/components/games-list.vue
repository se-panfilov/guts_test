<template>
  <div class='main-list'>
    <ul class='main-list__container'>
      <li v-for='g in games'>
        <img :src='getSrc(g.gameId)' alt='g.name'>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name: 'MainHeader',
    data () {
      return {
        search: '',
        games: [
          {
            'gameId': 8820,
            'name': '1 Can 2 Can',
            'shortDescription': 'Short Description',
            'slug': '1-can-2-can',
            'suggestedHeight': 3,
            'suggestedWidth': 4,
            'description': 'Description',
            'category': '',
            'gameType': 'Video Slots',
            'vendor': 'NYX Gaming',
            'inMaintenance': false
          },
          {
            'gameId': 9718,
            'name': '1429 Uncharted Seas',
            'shortDescription': 'Short Description',
            'slug': '1429-uncharted-seas',
            'suggestedHeight': 9,
            'suggestedWidth': 16,
            'description': 'Description',
            'category': '',
            'gameType': 'Video Slots',
            'vendor': 'NYX Gaming',
            'inMaintenance': false
          },
          {
            'gameId': 7989,
            'name': '2 Million B.C.',
            'shortDescription': 'Short Description',
            'slug': '2-million-bc',
            'suggestedHeight': 3,
            'suggestedWidth': 4,
            'description': 'Description',
            'category': '',
            'gameType': '3D Slots',
            'vendor': 'BetSoft',
            'inMaintenance': false
          }
        ]
      }
    },
    methods: {
      getSrc (id) {
        return `https://bay1.guts.im/newguts2/images/games/${id}.jpg`
      }
    }
  }
</script>

<style scoped>

</style>
