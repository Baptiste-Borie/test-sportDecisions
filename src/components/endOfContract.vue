<template>
    <div>
        <h1>Liste des Joueurs</h1>
            <div v-for="player in players" :key="player.id">
                <profileComponent :player="player" />
            </div>
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
