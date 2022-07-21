<template>
    <div :class="navType==='blocks' ? null : 'is-hidden'" class="wrapper has-background-black tile is-ancestor is-vertical mb-0">
        <div class="tile is-parent is-overlay">
            <div class="tile is-flex is-justify-content-center">
                <p class="title has-text-white">www.danielmorgan.xyz</p>
            </div>
        </div>
        <div class="tile is-parent is-align-items-center">
            <div class="tile is-4 is-flex is-justify-content-right">
                <nav>
                    <div class="tile is-vertical">
                        <NavItem :order="3" href="#" text="Portfolio" />
                        <NavItem :order="2" href="#" text="Games" />
                        <NavItem :order="1" href="#" text="About" />
                        <NavItem :order="0" href="#" text="Home" />
                    </div>
                </nav>
            </div>
            <div class="tile is-8 is-flex is-justify-content-center">
                <div>
                    <h1 class="title is-size-1 has-text-white has-text-weight-bold">
                        {{text}}
                    </h1>
                    <div class="underline"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
    import NavItem from './NavItem.vue';

    export default {
        name: 'MainHeader',
        components: {
            NavItem
        },
        props: {    
            textList: Array
        },
        data() {
            return {
                text:"Header",
                navType:"blocks"
            }
        },
        created() {
            this.text = this.textList[Math.floor(Math.random()*this.textList.length)];
        }
    }
</script>

<style lang="scss" scoped>
    @import "../assets/main.scss";
    .wrapper {
        height: 100vh;
    }
    .underline {
        width: 100%;
        height: 10px;
        position: relative;
        top: -20%;
        background-color: $secondary;
    }
</style>