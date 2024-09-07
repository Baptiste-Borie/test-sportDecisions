<template>
    <div class="menuWrapper d-flex">
        <button type="button" class="button">
            <chevronLeft/>
        </button>
        <div class=" menuOptions col-col-5" v-for="(option, index) in menuOptions" :key="index">{{ option }}</div>
        <button class="button">
            <chevronRight/>
        </button>
    </div>
</template>

<script>
  import { MENU } from '../constant/constant'
  import  chevronRight from '../assets/chevronRight.vue'
  import chevronLeft from '../assets/chevronLeft.vue'

export default{
    name: "headerMenu",
    components:{
        chevronRight,
        chevronLeft
    },
    props:{
        option: String
    },
    data() {
        return {
            menuOptions: MENU
        }
    }
}
</script>

<style scoped>
    .button{
        background-color: #64b8e2ac;
        border: 0;
    }
    .menuWrapper{
        flex-direction: row;
        justify-content: space-around;
        color: #64b7e2;
        border: 5px solid #64b8e2ac;
        border-radius: 5px;
    }
    .menuOptions {
        flex: 1;
        border: 3px solid #64b8e2ac;
    }
</style>