<template>
    <div class="is-relative is-clipped">
        <div style="padding-top: 10vmax"></div>
        <div class="sky-container is-clipped">
            <MainWave colour="#181a1bff" :isFlipped="true">
                <MainWave colour="rgb(84, 103, 169)" :isOverlay="true" top="10px" left="0px" rotation="0deg" :isFlipped="true">
                    <MainWave colour="rgb(202,118,28)" :isOverlay="true" top="0px" left="0px" rotation="2deg" :isFlipped="true"></MainWave>
                </MainWave>
            </MainWave>
            <div class="shine-path is-clipped">
                <div class="shine is-clipped is-overlay"></div>
                <div class="skill-scroller--top">
                    <img class="skill" src="../../assets/icons/c.svg"/>
                    <img class="skill" src="../../assets/icons/css.svg"/>
                    <img class="skill" src="../../assets/icons/git.svg"/>
                    <img class="skill" src="../../assets/icons/html.svg"/>
                    <img class="skill" src="../../assets/icons/instagram.svg"/>
                    <img class="skill" src="../../assets/icons/javascript.svg"/>
                    <img class="skill" src="../../assets/icons/node.svg"/>
                    <img class="skill" src="../../assets/icons/npm.svg"/>
                    <img class="skill" src="../../assets/icons/python.svg"/>
                    <img class="skill" src="../../assets/icons/raspberrypi.svg"/>
                    <img class="skill" src="../../assets/icons/scss.svg"/>
                    <img class="skill" src="../../assets/icons/tailwind.svg"/>
                    <img class="skill" src="../../assets/icons/unity.svg"/>
                    <img class="skill" src="../../assets/icons/vscode.svg"/>
                    <img class="skill" src="../../assets/icons/vue.svg"/>
                </div>
                <div class="skill-scroller--bottom">
                    <img class="skill" src="../../assets/icons/c.svg"/>
                    <img class="skill" src="../../assets/icons/css.svg"/>
                    <img class="skill" src="../../assets/icons/git.svg"/>
                    <img class="skill" src="../../assets/icons/html.svg"/>
                    <img class="skill" src="../../assets/icons/instagram.svg"/>
                    <img class="skill" src="../../assets/icons/javascript.svg"/>
                    <img class="skill" src="../../assets/icons/node.svg"/>
                    <img class="skill" src="../../assets/icons/npm.svg"/>
                    <img class="skill" src="../../assets/icons/python.svg"/>
                    <img class="skill" src="../../assets/icons/raspberrypi.svg"/>
                    <img class="skill" src="../../assets/icons/scss.svg"/>
                    <img class="skill" src="../../assets/icons/tailwind.svg"/>
                    <img class="skill" src="../../assets/icons/unity.svg"/>
                    <img class="skill" src="../../assets/icons/vscode.svg"/>
                    <img class="skill" src="../../assets/icons/vue.svg"/>
                </div>
            </div>
            <MainWave colour="#181a1bff" :isFlipped="false">
                <MainWave colour="rgb(84, 103, 169)" :isOverlay="true" top="-10px" left="0px" rotation="0deg" :isFlipped="false">
                    <MainWave colour="rgb(202,118,28)" :isOverlay="true" top="-5px" left="0px" rotation="2deg" :isFlipped="false"></MainWave>
                </MainWave>
            </MainWave>
        </div>
        <MainSectionHeading text="Skills"></MainSectionHeading>
    </div>
</template>

<script>
    import MainWave from "../MainWave";
    import MainSectionHeading from "../MainSectionHeading";
    export default {
        name:"SkillScroller",
        components: {
            MainWave,
            MainSectionHeading
        },
    }
</script>

<style lang="scss" scoped>
    @import "../../assets/main.scss";

    $skillWidth: 10vh;

    .shine-path {
        width: 100vw;
        transform: rotateZ(5deg);
    }
    .shine {
        width: 100vw;
        height: 1rem;
        background-color: $secondary;
        top:50%;
    }
    @keyframes slide {
        0% {
            left:-$skillWidth;
        }
        100% {
            left:258vh;
        }
    }
    .skill-scroller {
        position:relative;
        display: flex;
        flex-wrap: nowrap;
        height: $skillWidth;
        width: 100%;
        &--top {
            @extend .skill-scroller;
            transform: translateY($skillWidth/2);
        }
        &--bottom {
            @extend .skill-scroller;
            transform: translateY(-$skillWidth/2) translateX(-268vh);
        }
    }
    .skill {
        margin-inline: 4vh;
        width:$skillWidth;
        position:relative;
        animation: slide 40s linear 0s infinite;
        filter: drop-shadow(5px 4px 2px $primary);
    }
    @keyframes slide-sky {
        from {
            background-position-x: 0%;
        }
        to {
            background-position-x: -100%;
        }
    }
    .sky-container {
        background-image: url("../../assets/sky.svg");
        background-repeat: repeat;
        background-size: 30vmin;
        animation: slide-sky 50s linear 0s infinite;
    }
</style>