<template>
    <div class="player-profile">
        <h2>{{ player.nickname }}</h2>
        <p>Position : {{ player.position }}</p>
    </div>
</template>

<script>
export default {
    name: "profileComponent",
    props: {
        player: Object
    }
}
</script>

<style scoped>
.player-profile {
    border: 1px solid #ccc;
    padding: 20px;
    margin-bottom: 20px;
}
</style>