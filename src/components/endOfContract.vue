<template>
    <div>
        <h1>Liste des Joueurs</h1>
            <div class="container">
        <div class="row">
          <div class="col col-5 border-0"></div>
          <div v-for="(option, index) in menuOptions" :key="'menu-' + index" class="col col-2 border-0">
            <header-menu :option="option" />
          </div>
        </div>
  
        <div v-for="(player, index) in players" :key="'player-' + index" class="row">
          <div class="col col-5">
            <profile-component :player="player" />
          </div>
          <div class="col col-2"></div>
          <div class="col col-2"></div>
          <div class="col col-2"></div>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import data from '../store/data.json'
  import profileComponent from './profileComponent.vue'
  import headerMenu from './headerMenu.vue'
  import { MENU } from '../constant/constant'
  
  export default {
    name: "endOfContract",  
    components: {
      profileComponent,
      headerMenu,
    },
    data() {
      return {
        players: data.players,
        menuOptions: MENU,
      }
    }
  }
  </script>
  
  <style scoped>
  .col {
    border-bottom: 1px dashed #003957;
  }

  </style>
  