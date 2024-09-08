<template>
  <table class="table table-hover">
    <thead class="table-dark">
      <tr>
        <th class="col-md-3 col-sm-12"></th>
        <th class="col-md-9 col-sm-12" colspan="3">
          <header-menu @change="handleMenuChange" /> 
        </th>
      </tr>
    </thead>
    <tbody class="table-dark">
      <tr v-for="(player, index) in players" :key="'player-' + index">
        <th scope="row" class="col-md-3 col-sm-6">
          <profile-component :player="player" />
        </th>

        <td class="date col-md-3 col-sm-6" v-if="windowWidth > 768 || currentIndex === 0">
          <div class="dateDiv" :style="{color: player.contract_end_status || 'white'}">
            {{ player.contract_end }}
          </div>
        </td>

        <td class="date col-md-3 col-sm-12" v-if="windowWidth > 768 || currentIndex === 1">
          {{ player.option }}
        </td>
        <td class="date col-md-3 col-sm-12" v-if="windowWidth > 768 || currentIndex === 2">
          <div> {{ player.option_validity }} </div>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import data from '../store/data.json'
import profileComponent from './profileComponent.vue'
import headerMenu from './headerMenu.vue'

export default {
  name: "endOfContract",
  components: {
    profileComponent,
    headerMenu,
  },
  data() {
    return {
      players: data.players,
      windowWidth: window.innerWidth,
      currentIndex: 0,
    }
  },
  methods: {
    handleMenuChange(index) {
      this.currentIndex = index;
      }
  },
  mounted() {
    window.addEventListener('resize', () => {
      this.windowWidth = window.innerWidth
    });
  }
}
</script>

  
  <style scoped>

  .col {
    border-bottom: 1px dashed #003957;
  }

  .date {
    color: white;
    vertical-align: middle;
    align-content: center;
  }
  </style>