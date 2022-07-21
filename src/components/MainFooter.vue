<template>
    <div class="is-flex is-flex-direction-column is-justify-content-space-evenly has-background-black wrapper">
        <div class="is-flex is-justify-content-space-evenly is-align-items-center">
            <div>
                <h1 class="has-text-white">
                    {{text}}
                </h1>
            </div>
            <div>
                <h1 class="has-text-white">
                    {{text}}
                </h1>
            </div>
        </div>
        <div class="is-flex is-justify-content-center">
            <a href="https://github.com/dmrgn" class="is-flex is-justify-content-baseline has-text-white">Created By Daniel Morgan
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
    .wrapper {
        height: 20vh;
    }
</style>