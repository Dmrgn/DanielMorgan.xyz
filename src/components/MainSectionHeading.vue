<template>
    <!-- mobile -->
    <div :class="$root.width > $root.height || !$root.isMobile ? '' : 'is-mobile'" class="wrapper is-overlay">
        <div class="is-relative">
            <img class="sign" src="../assets/arrow.svg" />
            <h1 :class="$root.isMobile ? 'is-mobile' : ''" class="text has-text-white">{{text}}</h1>
        </div>
    </div>
</template>

<script>
    export default {
        name:"MainSectionHeading",
        props: {
            text: {
                type: String,
                default: "Heading" 
            },
        },
    }
</script>

<style lang="scss" scoped>
    .wrapper {
        transition: all 0.5s;
        transform: translateY(10vw) translateX(calc(50vw - 25vmin)) rotate(10deg);
    }
    .wrapper.is-mobile {
        transition: all 0.5s;
        transform: translateY(10vw) translateX(2vw) rotate(10deg);
    }
    .sign {
        width: #{"max(40vmin, 300px)"};
    }
    .text {
        position: absolute;
        font-size: #{"max(2vmax, 2rem)"};
        top: 33%;
        left: #{"max(4vmax, 3rem)"};
    }
</style>