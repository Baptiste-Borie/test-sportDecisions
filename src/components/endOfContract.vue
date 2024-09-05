<template>
    <div>
        <h1>Liste des Joueurs</h1>
        <profile-component v-for="player in players" :key="player.id" :player="player"/>
    </div>
</template>

<script>
import { players } from '../store/data.json'
import profileComponent from './profileComponent.vue'

export default {
    name: "endOfContract",
    components: {
        profileComponent,
    },
    data() {
        return {
            players,
        }
    }
}
</script>