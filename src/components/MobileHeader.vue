<template>
    <nav class="navbar has-background-black has-text-white" role="navigation" aria-label="main navigation">
        <div class="navbar-brand">
            <a class="navbar-item" href="/">
                {{text}}
            </a>
            <a role="button" class="navbar-burger burger" aria-label="menu" aria-expanded="false" data-target="navbarBasicExample">
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
                <span aria-hidden="true"></span>
            </a>
        </div>

        <div id="navbarBasicExample" class="navbar-menu">
            <div class="navbar-start">
                <a class="navbar-item">
                    Home
                </a>
                <a class="navbar-item">
                    About
                </a>
                <a class="navbar-link">
                    Games
                </a>
                <a class="navbar-link">
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
}
</script>

<style lang="scss" scoped>

</style>