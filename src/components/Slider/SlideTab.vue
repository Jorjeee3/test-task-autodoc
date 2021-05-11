<template>
    <nav class="slider-navigation">
        <button v-for="(tab, tabIndex) in tabs" :key="tab.tabTitle" :class="{ active: isActive(tabIndex) }" class="tab-button">
            <small class="tab-number">0{{tabIndex + 1}}</small>
            <h3 class="tab-title">{{tab.tabTitle}}</h3>
        </button>
    </nav>
</template>

<script>
export default {
    props: {
        tabs: {
            type: Array,
            required: true,
        },
        currentSlideIndex: {
            type: Number,
            required: true,
        },
    },
    
    methods: {
        isActive(tabIndex) {
            return this.currentSlideIndex === tabIndex
        }
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
    padding-bottom: 20px;
    background-color: #F8F8F8;
    border: 0;
    border-right: 1px solid #c6caca;
}

.tab-button.active {
    padding-top: 30px;
    background-color: #D2231A;
    color: #fff;
}

.tab-number {
    display: inline-block;
    vertical-align: baseline;
    color: #c6caca;
}

.tab-title {
    display: inline-block;
    vertical-align: baseline;
    width: 90%;
    margin: 10px 0;
    font-weight: 500;
    font-size: 16px;
}
</style>