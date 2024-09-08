<template>
    <div class="menuWrapper d-flex">
        <button type="button" class="button" @click="prevOption">
            <chevronLeft class="chevron"/>
        </button>
        <div class="menuOptions col-col-5" v-for="(option, index) in filteredOptions" :key="index">{{ option }}</div>
        <button class="button" @click="nextOption">
            <chevronRight class="chevron"/>
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
            menuOptions: MENU,
            currentIndex: 0,
            windowWidth: window.innerWidth,
        }
    },
    computed: {
        filteredOptions() {
            if (this.windowWidth >= 768) {
                return this.menuOptions.slice(0, 3);
            } else {
                return this.menuOptions.slice(this.currentIndex, this.currentIndex + 1);
            }        
        }
    },
    methods: {
        prevOption() {
            if (this.currentIndex > 0) {
                this.currentIndex--;
                this.$emit('change', this.currentIndex);
            }
        },
        nextOption() {
            if (this.currentIndex < this.menuOptions.length - 1) {
                this.currentIndex++;
                this.$emit('change', this.currentIndex);
            }
        }
    },
    mounted() {
        window.addEventListener('resize', () => {
        this.windowWidth = window.innerWidth
        })
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

    @media (min-width: 767px) {
        .button {
            pointer-events: none; 
        }
        .chevron{
            visibility: hidden;
        }
    }
    @media (max-width: 767px) {
        .menuOptions {
            padding: 0px 20px 15px;
            width: 100%;
        }
    }
</style>