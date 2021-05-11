<template>
    <button
        :class="{ active: isActive }"
        class="tab-button"
        @click="setActiveTab"
    >
        <ProgressBar
            :animationDuration="animationDuration"
            v-if="isActive"
            class="progress-bar"
        />
        <h3 class="tab-title">
            <small class="tab-number">0{{tabIndex + 1}}</small>
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
        tab:{
            type: Object,
            required: true,
        },
        animationDuration: {
			type: Number,
			default: 0
		}
    },
    
    methods: {
        setActiveTab() {
            this.$emit("set-active-tab", this.tabIndex)
        }
    },

    components: {
        ProgressBar
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

.tab-button {
    flex-grow: 1;
    flex-basis: 0;
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