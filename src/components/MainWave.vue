<template>
    <div :style="`top:${top};left:${left};transform:rotate(${rotation});`" :class="($root.isMobile?'is-mobile':'is-clipped')+' '+(isOverlay?'is-overlay':'')" class="svg-clip">
        <slot></slot>
        <svg :class="(isFlipped?'flipped':'unflipped')" class="wave" width="100%" :height="$root.isMobile?'200%':'100%'">
            <!-- Create mask that we'll use to define a slight gradient -->
            <defs :id="`fade${uid}`">
                <linearGradient :id="`sw-gradient-${uid}`" x1="0" y1="0" x2="0" y2="100%">
                    <stop :stop-color="colour" offset="0%"></stop>
                    <stop :stop-color="colour" offset="100%"></stop>
                </linearGradient>
                <rect :fill="`url(#sw-gradient-${uid})`" width="100%" height="100%"></rect>
            </defs>
            <pattern :id="`pattern-wave-${uid}`" x="0" y="0" width="1440" height="1000" patternUnits="userSpaceOnUse">
                <path :mask="`url(#fade${uid})`" :fill="`url(#sw-gradient-${uid})`"
                    d="M0,108L0,135C10,150,40,144,60,166.5C80,189,100,216,120,216C140,216,160,189,180,162C200,135,220,108,240,85.5C260,63,280,45,300,54C320,63,340,99,360,121.5C380,144,400,153,420,148.5C440,144,460,126,480,112.5C500,99,520,90,540,85.5C560,81,580,81,600,90C620,99,640,117,660,144C680,171,700,207,720,216C740,225,760,207,780,180C800,153,820,117,840,117C860,117,880,153,900,139.5C920,126,940,63,960,54C980,45,1000,90,1020,117C1040,144,1060,153,1080,130.5C1100,108,1120,54,1140,49.5C1160,45,1180,90,1200,94.5C1220,99,1240,63,1260,58.5C1280,54,1300,81,1320,81C1340,81,1360,54,1380,58.5C1400,63,1420,99,1430,117L1440,135L1440,270L1430,270C1420,270,1400,270,1380,270C1360,270,1340,270,1320,270C1300,270,1280,270,1260,270C1240,270,1220,270,1200,270C1180,270,1160,270,1140,270C1120,270,1100,270,1080,270C1060,270,1040,270,1020,270C1000,270,980,270,960,270C940,270,920,270,900,270C880,270,860,270,840,270C820,270,800,270,780,270C760,270,740,270,720,270C700,270,680,270,660,270C640,270,620,270,600,270C580,270,560,270,540,270C520,270,500,270,480,270C460,270,440,270,420,270C400,270,380,270,360,270C340,270,320,270,300,270C280,270,260,270,240,270C220,270,200,270,180,270C160,270,140,270,120,270C100,270,80,270,60,270C40,270,20,270,10,270L0,270Z"></path>
            </pattern>
            <!-- The canvas with our applied pattern -->
            <rect x="0" y="0" width="100%" height="100%" :fill="`url(#pattern-wave-${uid})`"></rect>
        </svg>
    </div>
</template>


<script>
    export default {
        name: "MainWave",
        data() {
            return {
                uid: 0
            }
        },
        props: {
            colour: String,
            isFlipped: Boolean,
            isOverlay: Boolean,
            top: String,
            left: String,
            rotation: String,
        },
        mounted () {
            this.uid = Math.floor(Math.random()*1000);
        },
    }
</script>

<style lang="scss" scoped>
    .svg-clip.is-mobile {
        height: 125px;
        transform: scaleY(0.6) translateY(-50%);
    }
    .svg-clip {
        height: 250px;
        transform: scaleY(1) translateY(0);
    }

    .wave {
        transition: 0.3s;
    }

    .flipped{
        transform: rotate(180deg);
    }
    .unflipped{
        transform: rotate(0deg);
    }
</style>