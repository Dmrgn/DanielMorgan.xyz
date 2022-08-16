<template>
    <div class="section">
        <AboutSection></AboutSection>
    </div>
    <SkillScroller></SkillScroller>
</template>

<script>

import SkillScroller from '../homepage/SkillScroller.vue';
import AboutSection from '../homepage/AboutSection.vue';

export default {
    name:"HomePage",
    components: {
        SkillScroller,
        AboutSection
    },
}
</script>

<style lang="scss" scoped>

</style>