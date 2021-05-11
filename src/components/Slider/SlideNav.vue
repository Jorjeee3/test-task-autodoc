<template>
    <nav class="slider-navigation">
        <SlideTab v-for="(tab, tabIndex) in tabs"
            :key="tab.tabTitle"
            @set-active-tab="setActiveTab"
            :tabIndex="tabIndex" 
            :currentSlideIndex="currentSlideIndex"
            :tab="tab"
            :isActive="isActive(tabIndex)"
            :animationDuration="animationDuration"
        />  
    </nav>
</template>

<script>
import SlideTab from './SlideTab.vue';

export default {
    name: "SlideNav",
    props: {
        tabs: {
            type: Array,
            required: true,
        },
        currentSlideIndex: {
            type: Number,
            required: true,
        },
        animationDuration: {
			type: Number,
			default: 0
		}
    },
    
    methods: {
        isActive(tabIndex) {
            return this.currentSlideIndex === tabIndex
        },
        clickActiveButton(tabIndex) {
            return this.currentSlideIndex === tabIndex
        },
        setActiveTab (tabIndex) {
            this.$emit("set-active-tab", tabIndex)
        }

    },

    components: {
        SlideTab,
    }
}
</script>

<style scoped>
.slider-navigation {
    display: flex;
    flex-direction: row;
    align-items: flex-end;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
}

</style>