<template>
  <table class="table">
    <thead class="table-dark">
      <tr>
        <th class="col-3"></th>
        <th class="col-9" colspan="3" >
          <header-menu />
        </th>
      </tr>
    </thead>
    <tbody class="table-dark">
      <tr v-for="(player, index) in players" :key="'player-' + index">
        <th scope="row" class="col-3">
          <profile-component :player="player" />
        </th>
        <td class="date col-3">
          <div :style="{color: player.contract_end_status || 'white'}">
            {{ player.contract_end }}
          </div>
        </td>
        <td class="date col-3">
          <div>
            {{ player.option }}
          </div>
        </td>
        <td class="date col-3">
          <div>
            {{ player.option_validity }}
          </div>
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
      }
    }
  }
  </script>
  
  <style scoped>

  .col {
    border-bottom: 1px dashed #003957;
  }

  .date {
    margin-top: 15px;
    align-items: center;
    justify-content: center;
    color: white;
  }
  </style>
  