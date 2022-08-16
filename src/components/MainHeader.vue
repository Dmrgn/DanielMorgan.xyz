<template>
    <div :class="navType==='blocks' ? null : 'is-hidden'" class="wrapper has-background-black tile is-ancestor is-vertical mb-0">
        <div class="tile is-parent is-overlay">
            <div class="tile is-flex is-justify-content-center is-unselectable" @click="$root.copyToClipboard('https://danielmorgan.xyz')">
                <p class="title has-text-white">www.danielmorgan.xyz</p>
            </div>
        </div>
        <img :class="$root.scrollAmount > 0.05 ? 'faded-away' : ''" class="scroll-prompt is-overlay" src="../assets/scrollprompt.png" />
        <div class="tile is-parent is-align-items-center">
            <div class="tile is-4 is-flex is-justify-content-right">
                <nav>
                    <div class="tile is-vertical">
                        <NavItem :order="1" href="#" text="Portfolio" />
                        <NavItem :order="0" href="#" text="Home" />
                    </div>
                </nav>
            </div>
            <div class="tile is-8 is-flex is-justify-content-center">
                <div>
                    <h1 class="title is-size-1 has-text-white has-text-weight-bold is-unselectable is-hoverable-text">
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
    @keyframes grow {
        from {
            width: 0%;
        }
        to {
            width: 100%;
        }
    }
    .underline {
        width: 0%;
        height: 10px;
        position: relative;
        top: -20%;
        background-color: $secondary;
        animation: 0.5s ease-in-out 0.4s 1 forwards grow;
    }
    .scroll-prompt {
        transition: transform 0.2s;
        filter: invert(30%);
        top: 90%;
        left: calc(50% - 32px);
        transform: scale(1.0);
    }
    .is-hoverable-text {
        transition: font-size 1s;
    }
    .is-hoverable-text:hover {
        font-size: 5vh !important;
    }
    .faded-away {
        transform: scale(0);
    }
</style>