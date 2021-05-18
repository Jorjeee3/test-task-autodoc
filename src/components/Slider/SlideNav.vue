<template>
    <nav class="slider-navigation">
        <SlideTab 
            v-for="(tab, tabIndex) in tabs"
            :key="tab.tabTitle"
            :tabIndex="tabIndex" 
            :currentSlideIndex="currentSlideIndex"
            :tab="tab"
            :autoStart="autoStart"
            :sliderStopped="sliderStopped"
            :isActive="isActive(tabIndex)"
            :animationDuration="animationDuration"
            @start-slider="startSlider"
            @set-active-tab="setActiveTab"
            @stop-slider="stopSlider"
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
		},
        sliderStopped: {
			type: Boolean,
			required: true, 
		},
        autoStart: {
            type: Boolean,
			required: true,
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
        },
        startSlider() {
            this.$emit("start-slider")
        },
        stopSlider () {
            this.$emit("stop-slider")
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
    overflow-x: auto;
    white-space: nowrap;
    position: absolute;
    left: 0;
    bottom: 0;
    width: 100%;
}

</style>