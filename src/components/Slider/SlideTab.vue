<template>
    <button
        :class="{ active: isActive }"
        class="tab-button"
        @click="setActiveTab"
        @mouseover="stopSlider"
        @mouseleave="startSlider"
    >
        <ProgressBar
            :animationDuration="animationDuration"
            v-if="isActive && autoStart"
            class="progress-bar"
            :start="!sliderStopped"
        />
        <h3 class="tab-title">
            <small class="tab-number" v-if="twoDigits">{{twoDigits}}</small>
            {{tab.tabTitle}}
        </h3>
    </button>
</template>

<script>
import ProgressBar from '@/components/progress/ProgressBar/ProgressBar.vue';

export default {
    name: "SlideTab",
    props: {
        tabIndex: {
            type: Number,
            required: true,
        },
        isActive: {
            type: Boolean,
            required: true,
        },
        tab: {
            type: Object,
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
        setActiveTab() {
            this.$emit("set-active-tab", this.tabIndex)
        },
        startSlider() {
            this.$emit("start-slider")
        },
        stopSlider () {
            this.$emit("stop-slider")
        }
    },
    computed: {
        twoDigits() {
            let { tabIndex } = this 
            tabIndex++;

            if (tabIndex < 10) {
                return '0' + tabIndex
            } 
            return tabIndex
        }
    },
    components: {
        ProgressBar
    }
}
</script>

<style scoped>
.tab-button {
    flex-grow: 1;
    flex-basis: 0;
    flex: 1;
    padding-bottom: 20px;
    background-color: #F8F8F8;
    border: 0;
    border-right: 1px solid #c6caca;
    cursor: pointer;

    --progress-bar-background-color: rgba(255, 255, 255, 0.6);
}

.tab-button.active {
    padding-top: 10px;
    background-color: #D2231A;
    color: #fff;
    cursor: inherit;
}

.tab-button.active .progress-bar {
    margin: 0 0 10px;
}

.tab-number {
    color: #c6caca;
    position: absolute;
    top: 2px;
    left: 0px;
}

.tab-title {
    display: block;
    width: 100%;
    margin: 10px 0;
    font-weight: 500;
    font-size: 16px;
    position: relative;
    padding: 0 18px;
}
</style>