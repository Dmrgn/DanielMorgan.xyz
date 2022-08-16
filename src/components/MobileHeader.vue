<template>
    <nav class="navbar has-background-black has-text-white" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
            <a :class="$root.width < 350 ? 'is-size-6' : 'is-size-4' " class="navbar-item has-text-primary" href="/">
                {{text}}
            </a>
            <a @click="onClick" ref="burgerElement" role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false">
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
            </a>
        </div>

        <div ref="navbarElement" class="navbar-menu has-background-black has-text-white nav-menu">
            <div class="navbar-start">
                <a @click="this.navigateTo('Home')" class="navbar-item">
                    Home
                </a>
                <a @click="this.navigateTo('Portfolio')" class="navbar-item">
                    Portfolio
                </a>
            </div>
        </div>
    </nav>
</template>

<script>
export default {
    name: 'MobileHeader',
    components: {

    },
    props: {    
        textList: Array
    },
    data() {
        return {
            text:"Header"
        }
    },
    created() {
        this.text = this.textList[Math.floor(Math.random()*this.textList.length)];
    },
    methods: {
        onClick() {
            this.$refs.navbarElement.classList.toggle("is-active");
            this.$refs.burgerElement.classList.toggle("is-active");
        },
        navigateTo(page) {
            this.$root.currentPage = page;
            this.$refs.navbarElement.classList.toggle("is-active");
            this.$refs.burgerElement.classList.toggle("is-active");
        }
    },
}
</script>

<style lang="scss" scoped>
    @import "../assets/main.scss";
    .navbar-item {
        color: white;
    }
    .navbar-item:hover {
        background-color: lighten($black, 10%) !important;
    }
</style>