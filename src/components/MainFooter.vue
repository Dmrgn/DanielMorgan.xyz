<template>
    <div class="tile is-flex-direction-column is-justify-content-center has-background-black section">
        <div class="tile is-parent is-justify-content-space-around is-align-items-center">
            <div class="tile is-child link footer-item">
                Icons by <a class="has-text-white link" href="https://icons8.com/">Icons8.com</a>
            </div>
            <div class="tile is-child link footer-item">
                <a class="has-text-white link" href="#top-elm">Return to top</a>
            </div>
            <div class="tile is-child">
                <h1 class="has-text-white footer-item">
                    {{text}}
                </h1>
            </div>
        </div>
        <div class="tile is-parent is-justify-content-center">
            <a href="https://github.com/dmrgn" class="is-flex is-justify-content-center has-text-white">Created By Daniel Morgan
                <img class="icon ml-2" src="https://cdn-icons-png.flaticon.com/512/25/25231.png"/>
            </a>
        </div>
    </div>
</template>

<script>

    export default {
        name: 'MainFooter',
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
        }
    }
</script>

<style lang="scss" scoped>
    .footer-item {
        text-align: center;
    }
    .link:hover {
        transform: scale(1.25, 1.25);
    }
    .link {
        transition: transform 1s;
        transform: scaleX(1) scaleY(1);
    }
</style>