<template>
    <MainAbout></MainAbout>
    <SkillScroller></SkillScroller>
</template>

<script>

import SkillScroller from '../SkillScroller.vue';
import MainAbout from '../MainAbout.vue';

export default {
    name:"HomePage",
    components: {
        SkillScroller,
        MainAbout
    },
}
</script>

<style lang="scss" scoped>

</style>