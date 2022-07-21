<template>
    <div class="has-background-black">
        <MainHeader v-if="!isMobile" :textList="['Welcome!', 'Hello Human!', 'What\'s Up!']"/>
        <MobileHeader v-else :textList="['www.danielmorgan.xyz']"/>

        <HomePage v-if="currentPage=='Home'"/>
        <AboutPage v-else-if="currentPage=='About'"/>
        <GamesPage v-else-if="currentPage=='Games'"/>
        <PortfolioPage v-else-if="currentPage=='Portfolio'"/>

        <MainNotification v-if="isNotification" :isMobile="isMobile"> hello </MainNotification>
        
        <MainFooter :textList="['Welcome!', 'Hello Human!', 'What\'s Up!']"/>
    </div>
</template>

<script>
import MobileHeader from './components/MobileHeader.vue'
import MainHeader from './components/MainHeader.vue'
import MainNotification from './components/MainNotification.vue'
// import MainWave from './components/MainWave.vue'
import MainFooter from './components/MainFooter.vue'
import HomePage from './components/pages/HomePage.vue'
import AboutPage from './components/pages/AboutPage.vue'
import GamesPage from './components/pages/GamesPage.vue'
import PortfolioPage from './components/pages/PortfolioPage.vue'

export default {
    name: 'App',
    components: {
        MainHeader,
        // MainWave,
        MobileHeader,
        MainFooter,
        HomePage,
        MainNotification,
        AboutPage,
        GamesPage,
        PortfolioPage
    },
    data() {
        return {
            currentPage:"Home",
            isMobile:false,
            isNotification:false,
            width: 0,
            height: 0
        }
    },
    mounted () {
        window.onresize = this.resize;
        this.resize();
        this.currentPage = sessionStorage.lastPageVisited ?? "Home";
    },
    watch: {
        currentPage(newValue) {
            sessionStorage.lastPageVisited = newValue;
        }
    },
    methods: {
        resize() {
            this.isMobile = (window.innerWidth <= 900);
            this.width = window.innerWidth;
            this.height = window.innerHeight;
        }
    },
}
</script>

<style lang="scss">
    @import "./assets/main.scss";
    body {
        background-color: $black;
    }
</style>