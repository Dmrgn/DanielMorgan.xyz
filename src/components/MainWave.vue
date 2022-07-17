<template>
    <div class="svg-clip is-full">
        <!-- <svg :class="isFlipped?'flipped':'unflipped'" class="wave" viewBox="0 0 1440 320" version="1.1"
            xmlns="http://www.w3.org/2000/svg">
            <mask maskUnits="userSpaceOnUse" id="fade">
                <linearGradient id="sw-gradient-0" x1="0" x2="0" y1="1" y2="0">
                    <stop :stop-color="startColor" offset="0%"></stop>
                    <stop :stop-color="startColor" offset="100%"></stop>
                </linearGradient>
                <rect fill="url(#sw-gradient-0)" width="100%" height="100%"></rect>
            </mask>
            <pattern id="pattern-wave" x="0" y="0" width="1440" height="320" patternUnits="userSpaceOnUse">
                <path style="transform:translate(100%, 50%) rotate(180deg); opacity:1" fill="url(#sw-gradient-0)"
                    d="M0,72L10,84C20,96,40,120,60,132C80,144,100,144,120,123C140,102,160,60,180,60C200,60,220,102,240,114C260,126,280,108,300,105C320,102,340,114,360,126C380,138,400,150,420,129C440,108,460,54,480,45C500,36,520,72,540,96C560,120,580,132,600,129C620,126,640,108,660,99C680,90,700,90,720,75C740,60,760,30,780,24C800,18,820,36,840,45C860,54,880,54,900,48C920,42,940,30,960,42C980,54,1000,90,1020,102C1040,114,1060,102,1080,87C1100,72,1120,54,1140,54C1160,54,1180,72,1200,72C1220,72,1240,54,1260,48C1280,42,1300,48,1320,63C1340,78,1360,102,1380,93C1400,84,1420,42,1430,21L1440,0L1440,180L1430,180C1420,180,1400,180,1380,180C1360,180,1340,180,1320,180C1300,180,1280,180,1260,180C1240,180,1220,180,1200,180C1180,180,1160,180,1140,180C1120,180,1100,180,1080,180C1060,180,1040,180,1020,180C1000,180,980,180,960,180C940,180,920,180,900,180C880,180,860,180,840,180C820,180,800,180,780,180C760,180,740,180,720,180C700,180,680,180,660,180C640,180,620,180,600,180C580,180,560,180,540,180C520,180,500,180,480,180C460,180,440,180,420,180C400,180,380,180,360,180C340,180,320,180,300,180C280,180,260,180,240,180C220,180,200,180,180,180C160,180,140,180,120,180C100,180,80,180,60,180C40,180,20,180,10,180L0,180Z">
                </path>
            </pattern>
            <rect x="0" y="0" width="100%" height="100%" fill="url(#pattern-wave)"></rect>
        </svg> -->
        <svg :class="isFlipped?'flipped':'unflipped'" class="wave" width="100%" height="100%">
            <!-- Create mask that we'll use to define a slight gradient -->
            <defs id="fade">
                <linearGradient id="sw-gradient-0" x1="0" y1="0" x2="0" y2="100%">
                    <stop :stop-color="startColor" offset="0%"></stop>
                    <stop :stop-color="startColor" offset="100%"></stop>
                </linearGradient>
                <rect fill="url(#sw-gradient-0)" width="100%" height="100%"></rect>
            </defs>
            <pattern id="pattern-wave" x="0" y="0" width="1440" height="320" patternUnits="userSpaceOnUse">
                <path mask="url(#fade)" fill="url(#sw-gradient-0)"
                    d="M0,108L0,135C10,150,40,144,60,166.5C80,189,100,216,120,216C140,216,160,189,180,162C200,135,220,108,240,85.5C260,63,280,45,300,54C320,63,340,99,360,121.5C380,144,400,153,420,148.5C440,144,460,126,480,112.5C500,99,520,90,540,85.5C560,81,580,81,600,90C620,99,640,117,660,144C680,171,700,207,720,216C740,225,760,207,780,180C800,153,820,117,840,117C860,117,880,153,900,139.5C920,126,940,63,960,54C980,45,1000,90,1020,117C1040,144,1060,153,1080,130.5C1100,108,1120,54,1140,49.5C1160,45,1180,90,1200,94.5C1220,99,1240,63,1260,58.5C1280,54,1300,81,1320,81C1340,81,1360,54,1380,58.5C1400,63,1420,99,1430,117L1440,135L1440,270L1430,270C1420,270,1400,270,1380,270C1360,270,1340,270,1320,270C1300,270,1280,270,1260,270C1240,270,1220,270,1200,270C1180,270,1160,270,1140,270C1120,270,1100,270,1080,270C1060,270,1040,270,1020,270C1000,270,980,270,960,270C940,270,920,270,900,270C880,270,860,270,840,270C820,270,800,270,780,270C760,270,740,270,720,270C700,270,680,270,660,270C640,270,620,270,600,270C580,270,560,270,540,270C520,270,500,270,480,270C460,270,440,270,420,270C400,270,380,270,360,270C340,270,320,270,300,270C280,270,260,270,240,270C220,270,200,270,180,270C160,270,140,270,120,270C100,270,80,270,60,270C40,270,20,270,10,270L0,270Z"></path>
            </pattern>
            <!-- The canvas with our applied pattern -->
            <rect x="0" y="0" width="100%" height="100%" fill="url(#pattern-wave)"></rect>

        </svg>
    </div>
</template>


<script>
    export default {
        name: "MainWave",
        props: {
            startColor: String,
            stopColor: String,
            isFlipped: Boolean
        },
    }
</script>

<style lang="scss" scoped>
    .svg-clip {
        overflow: hidden;
        position: relative;
        top: 0px;
        left: 0;
        width: 100%;
        overflow: hidden;
        line-height: 0;
    }

    .wave {
        height: 240px;
        transition: 0.3s;
    }

    .flipped {
        transform: rotate(0deg);
    }

    .unflipped {
        transform: rotate(180deg);
    }
</style>