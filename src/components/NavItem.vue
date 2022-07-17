<template>
    <a :style="'--i:'+order+';'" href="#" @click="clicked">
        <div class="cube" :class="this.$root.currentPage == this.text ? 'clicked' : 'unclicked'">
            <div class="side--top"></div>
            <div class="sides">
                <span class="side--long" style="--i:0;">
                    <h2 class="has-text-black is-size-2 has-text-centered">
                        {{text}}
                    </h2>
                </span>
                <span class="side--short" style="--i:1;"></span>
                <span class="side--long" style="--i:2;">
                    <h2 class="has-text-black is-size-2 has-text-centered">
                        {{text}}
                    </h2>
                </span>
                <span class="side--short" style="--i:3;"></span>
            </div>
        </div>
    </a>
</template>

<script>
    export default {
        name: 'NavItem',
        props: {
            text: String,
            href: String,
            order: Number
        },
        methods: {
            clicked() {
                this.$root.currentPage = this.text;
            }
        },
        data() {
            return {
                className:"unclicked"
            }
        }
    }
</script>

<style lang="scss" scoped>
    @import "../assets/main.scss";

    $depth: 4vmin;
    $width: 15vmin;
    $height: 7.5vmin;

    a {
        order: var(--i);
    }
    @mixin cube-base {
        position: relative;
        transform-style: preserve-3d;
        width: $width;
        height: $height;
        transition: transform 1s;
    }
    .cube.unclicked {
        @include cube-base;
        transform: rotateX(-30deg) rotateY(30deg);
    }
    .cube.unclicked:hover {
        transform: rotateX(-30deg) rotateY(30deg) translateZ(40px);
    }
    .cube.clicked {
        @include cube-base;
        transform: rotateX(-30deg) rotateY(210deg);
    }
    .cube.clicked:hover {
        transform: rotateX(-30deg) rotateY(210deg) translateZ(-40px);
    }
    .sides {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        transform-style: preserve-3d;
    }
    .side {
        position: absolute;
        top: 0;
        height: 100%;
        transition: all 1s;
        background: $primary;
        &--long {
            @extend .side;
            left: -($width - $depth);
            width: $width*2;
            transform: rotateY(calc(90deg * var(--i))) translateZ($depth);
        }
        &--short {
            @extend .side;
            left: 0;
            width: $depth*2;
            background: darken($primary, 5%);
            transform: rotateY(calc(90deg * var(--i))) translateZ($width);
        }
        &--top {
            @extend .side;
            left: -($width - $depth);
            width: $width*2;
            height: $depth*2;
            background: none;
            background-color: darken($primary,10%);
            transform: rotateX(90deg) translateZ($depth);
        }
    }
    .cube.clicked > .sides > .side {
        background: $secondary;
    }
    .cube.clicked > .side {
        background: darken($secondary,10%);
    }
</style>