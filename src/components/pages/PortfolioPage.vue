<template>
    <div class="container section">
        <div class="is-flex is-align-items-center is-flex-direction-column mb-6">
            <h1 class="title has-text-white games-title">Portfolio</h1>
            <h3 class="has-text-centered">I'm constantly working on something new, check out 
                <a href="https://github.com/dmrgn" class="ml-2 is-flex is-justify-content-center has-text-white"> my GitHub!
                    <img class=" icon ml-2" src="https://cdn-icons-png.flaticon.com/512/25/25231.png"/>
                </a>
            </h3>
        </div>
        <div class="tile is-ancestor is-vertical projects-container">
            <div v-if="!$root.isMobile" class="clockwise-l"></div>
            <div class="tile" v-for="(row, index) in skillRows" :key="index">
                <div class="tile is-parent" v-for="(item, index) in row" :key="index">
                    <div class="tile is-child box has-background-primary is-flex is-flex-direction-column is-justify-content-space-between">
                        <div class="title mb-0 has-text-white">{{item.name}}</div>
                        <div class="techs my-2 is-flex">
                            <p class="px-2 has-background-white mr-2" v-for="(tag, index) in item.tags" :key="index">{{tag}}</p>
                        </div>
                        <div class="has-text-white">{{item.description}}</div>
                        <div class="mt-3">
                            <a v-if="item?.playLink" class="button mr-2" :href="item.playLink"><img class="mr-2" src="https://img.icons8.com/ios/20/000000/play--v1.png"/> Play</a>
                            <a v-if="item?.githubLink" class="button" :href="item.githubLink"><img class="mr-2" src="https://img.icons8.com/ios-glyphs/20/000000/github.png"/> GitHub</a>
                        </div>
                    </div>
                </div>
            </div>
            <div v-if="!$root.isMobile" class="counter-clockwise-l"></div>
        </div>
    </div>
</template>

<script>
import projects from "../../assets/json/projects.json";
export default {
    name:"GamesPage",
    data() {
        return {
            skillRows: []
        }
    },
    created () {
        this.skillRows = [];
        let stack = [];
        for (const project of projects) {
            stack.push(project);
            if (stack.length == 3) {
                this.skillRows.push([...stack]);
                stack = [];
            }
        }
        if (stack.length > 0)
            this.skillRows.push(stack);
    },
}
    </script>

<style lang="scss" scoped>
    @import "../../assets/main.scss";
    .has-background-secondary {
        background-color: $secondary;
        border-color: $secondary;
    }
    .games-title {
        font-size: 3rem;
    }
    .projects-container {
        position: relative;
    }
    @mixin l {
        content: "";
        position: absolute;
        background-color: $secondary;
        width: 1rem;
        height: 4rem;
    }
    .clockwise-l::before {
        @include l;
        left: -2rem;
        top: -2.2rem;
    }
    .clockwise-l::after {
        @include l;
        left: -2rem;
        top: -2.2rem;
        width: 4rem;
        height: 1rem;
    }
    .counter-clockwise-l::before {
        @include l;
        right: -2rem;
        bottom: -2.2rem;
    }
    .counter-clockwise-l::after {
        @include l;
        right: -2rem;
        bottom: -2.2rem;
        width: 4rem;
        height: 1rem;
    }
</style>