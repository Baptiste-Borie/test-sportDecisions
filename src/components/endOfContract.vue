<template>
  <table class="table table-hover">
    <thead class="table-dark">
      <tr>

        <th class="col-md-3 col-sm-12"></th> <!-- Fake table head to have an empty cell at [0,0] -->
        <th class="col-md-9 col-sm-12" colspan="3">
          <header-menu @change="handleMenuChange" ref="headerMenu" /> 
        </th>

      </tr>
    </thead>
    <tbody class="table-dark">
      <tr v-for="(player, index) in players" :key="'player-' + index">

        <th scope="row" class="col-md-3 col-sm-6">
          <profile-component :player="player" /> <!-- Player card -->
        </th>

        <td class="date col-md-3 col-sm-6" v-if="windowWidth > 768 || currentIndex === 0">
          <div class="dateDiv" :style="{color: player.contract_end_status || 'white'}">
            {{ player.contract_end }} <!-- END OF CONTRACT -->
          </div>
        </td>

        <td class="date col-md-3 col-sm-6" v-if="windowWidth > 768 || currentIndex === 1">
          {{ player.option }} <!-- OPTION -->
        </td>

        <td class="date col-md-3 col-sm-6" v-if="windowWidth > 768 || currentIndex === 2">
          <div> {{ player.option_validity }} </div> <!-- OPTION VALIDITY -->
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
      originalPlayers: [...data.players], // Copy of players in order to have a "clean" version of it
      windowWidth: window.innerWidth,
      currentIndex: 0,
      sortDirection: null
    }
  },
  methods: {
    handleMenuChange(index) {
      this.currentIndex = index;
      this.toggleSort(index);
    },
    toggleSort(index) {
      if (index === 0 && this.currentIndex === 0) {  // Sort is available only on "END OF CONTRACT" column 
        if (this.sortDirection === null) {
          this.sortDirection = 'asc';
          this.players.sort((a, b) => new Date(a.contract_end) - new Date(b.contract_end)); // Sort by ascent order
        } else if (this.sortDirection === 'asc') {
          this.sortDirection = 'desc';
          this.players.sort((a, b) => new Date(b.contract_end) - new Date(a.contract_end)); // Sort by descent order
        } else {
          this.sortDirection = null;
          this.players = [...this.originalPlayers]; // Reset order
        }

        // Emit sort direction to his children headerMenu
        this.$refs.headerMenu.updateSortDirection(this.sortDirection)
      }
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

  table.table-hover{
      border-bottom:1px dashed #003957;
      margin-top:20px;
    }

  table.table-hover > thead > tr > th{
      border-bottom: 0;
  }

  table.table-hover > tbody > tr > th{
      border-bottom:1px dashed #003957;
  }

  table.table-hover > tbody > tr > td{
      border-bottom:1px dashed #003957;
  }
  </style>