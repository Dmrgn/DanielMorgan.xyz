<template>
    <MainHeader v-if="!mobile" :textList="['Welcome!', 'Hello Human!', 'What\'s Up!']"/>
    <MobileHeader v-else :textList="['Hey!', 'Welcome!', 'Hello Human!', 'What\'s Up!']"/>
    <MainWave startColor="#181a1bff" stopColor="#26292bff" :isFlipped="false"></MainWave>
    
    <HomePage text="Welcome to my website, take a look around!"/>
    <MainWave startColor="#181a1bff" stopColor="#26292bff" :isFlipped="true"></MainWave>

    <MainWave startColor="#181a1bff" stopColor="#26292bff" :isFlipped="false"></MainWave>
    <MainFooter :textList="['Welcome!', 'Hello Human!', 'What\'s Up!']"/>
</template>

<script>
import MobileHeader from './components/MobileHeader.vue'
import MainHeader from './components/MainHeader.vue'
import MainWave from './components/MainWave.vue'
import MainFooter from './components/MainFooter.vue'
import HomePage from './components/HomePage.vue'

export default {
    name: 'App',
    components: {
        MainHeader,
        MainWave,
        MobileHeader,
        MainFooter,
        HomePage
    },
    data() {
        return {
            currentPage:"Home",
            mobile:false
        }
    },
    mounted () {
        window.onresize = this.resize;
        this.resize();
        this.currentPage = localStorage.lastPageVisited ?? "Home";
    },
    watch: {
        currentPage(newValue) {
            localStorage.lastPageVisited = newValue;
        }
    },
    methods: {
        resize() {
            this.mobile = (window.innerWidth <= 900);
        }
    },
}
</script>

<style lang="scss">
    @import "./assets/main.scss";
    body {
        background-color: $primary;
    }
</style>