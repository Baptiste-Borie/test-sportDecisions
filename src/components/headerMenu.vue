<template>
    <div class="menuWrapper d-flex">
        <button type="button" class="button" @click="prevOption">
            <chevronLeft class="chevron" v-if="currentIndex > 0"/>
        </button>
        <div class="menuOptions col-col-5" v-for="(option, index) in filteredOptions" :key="index" @click="selectOption(index)">
            {{ option }}
            <arrowUpShort v-if="currentIndex === 0 && index === 0 && localSortDirection === 'asc'" />
            <arrowDownShort v-if="currentIndex === 0 && index === 0 && localSortDirection === 'desc'" />
            <arrowEqual v-if="currentIndex === 0 && index === 0 && !localSortDirection" />
        </div> 
        <button class="button" @click="nextOption">
            <chevronRight class="chevron" v-if="currentIndex < 2"/>
        </button>
    </div>
</template>

<script>
    import { MENU } from '../constant/constant'
    import  chevronRight from '../assets/components/chevron/chevronRight.vue'
    import chevronLeft from '../assets/components/chevron/chevronLeft.vue'
    import arrowUpShort from "../assets/components/arrow/arrowUp.vue"
    import arrowEqual from "../assets/components/arrow/arrowEqual.vue"
    import arrowDownShort from "../assets/components/arrow/arrowDown.vue"

export default{
    name: "headerMenu",
    components:{
        chevronRight,
        chevronLeft,
        arrowUpShort,
        arrowDownShort,
        arrowEqual
        
    },
    props:{
        option: String ,// Define only if in mobile mode
        sortDirection: {
            type: String,
            default: null
        }
    },

    data() {
        return {
            menuOptions: MENU,
            currentIndex: 0,
            windowWidth: window.innerWidth,
            localSortDirection: this.sortDirection
        }
    },
    watch: {
    sortDirection(newVal) {
        this.localSortDirection = newVal;
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
        },
        selectOption(index) {
            this.$emit('change', index); 
        },
        updateSortDirection(direction) {
            this.localSortDirection  = direction;
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
        padding: 0px 20px 15px; 
        border: 3px solid #64b8e2ac;
        cursor: pointer;
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
            width: 100%;
        }
    }
</style>