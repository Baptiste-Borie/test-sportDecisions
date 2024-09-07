<template>
    <div id="playerProfile" class="p-2   d-flex align-items-flex-start text-white">
        <img src="../assets/ProfilePicture.png" alt="pictoplayer" class="rounded-circle me-2">
        <div id="info">
            <div id="name">{{ player.nickname }}</div>
            <div >Position : {{ player.position }}</div>
        </div>
        <threeDot class="threeDot"/>
    </div>
</template>

<script>
import threeDot from '../assets/threeDot.vue'
export default {
    name: "profileComponent",
    components:{
        threeDot
    },
    props: {
        player: Object
    }
}
</script>

<style scoped>
img{
    max-height: 100%;
}

#playerProfile {
    background-color: #003957;
    align-items: center;
    border-radius: 10px;
    font-size: 10px;
    height: 70px;
    margin: 15px 0 2px 2px
}

.threeDot {
    margin-left: auto;
}

#info > div {
    display: flex;
    justify-content: flex-start;
    color: rgb(200, 198, 198);
} 

#name {
    font-weight: bold;
    font-size: large;
    text-transform: uppercase;
}
</style>
