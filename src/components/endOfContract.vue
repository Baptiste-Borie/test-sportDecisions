<template>
        <div>
            <h1>Liste des Joueurs</h1>
            <div id="wrapperPlayer">
                <profile-component v-for="player in players" :key="player.id" :player="player"/>
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

<style scoped>

    #wrapperPlayer{
        margin: 5px;
        display: flex;
        flex-direction: column;
        gap: 5px;
    }
</style>