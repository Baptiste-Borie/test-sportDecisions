<template>
    <div id="playerProfile" class="m-1 m-top-2 p-2 d-flex align-items-flex-start text-white">
        <img src="../assets/ProfilePicture.png" alt="pictoplayer" class="rounded-circle me-2">
        <div id="info">
            <h2 class="fw-bold">{{ player.nickname }}</h2>
            <div >Position : {{ player.position }}</div>
        </div>
        <!-- Three dot icon from bootstrap https://icons.getbootstrap.com/icons/three-dots/ -->
        <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-three-dots" viewBox="0 0 16 16">
            <path d="M3 9.5a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3m5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3m5 0a1.5 1.5 0 1 1 0-3 1.5 1.5 0 0 1 0 3"/>
        </svg>
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
img{
    max-height: 100%;
}

#playerProfile {
    display: flex;
    flex-direction: row;
    background-color: #003957;
    align-items: center;
    border-radius: 10px;
    font-size: 10px;
    height: 70px;
}

#playerProfile > svg {
    margin-left: auto;
}

#info {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    padding:0px 10px
}

#info > div {
    display: flex;
    justify-content: flex-start;
    color: rgb(200, 198, 198);
} 
h2 {
    font-weight: bold;
}
</style>
