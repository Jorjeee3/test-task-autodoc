<template>
    <div class="slider">
        <transition name="fade" mode="out-in" tag="div">
            <Slide :key="slide.title" :slide="slide" />
        </transition>
        <SlideNav
            :tabs="slides"
            :currentSlideIndex="currentSlideIndex"
            @set-active-tab="setActiveTab" 
            :animationDuration="animationDuration"
        />
    </div>
</template>

<script>
import Slide from '@/components/Slider/Slide.vue';
import SlideNav from '@/components/Slider/SlideNav.vue'; 

export default {
    name: "Slider",
    data() {
        return {
            timer: null,
            currentSlideIndex: 0,
            animationDuration: 5000,
        };
    },
    props: {
        slides: {
            type: Array,
            required: true
        },
    },
    mounted () {
        this.startSlider();
    },

    methods: {
        startSlider () {
            this.timer = setInterval(this.next, this.animationDuration);
        },

        next () {
            if (this.currentSlideIndex === this.slides.length - 1) {
                this.currentSlideIndex = 0
            } else {
                this.currentSlideIndex += 1
            }
        },
        prev () {
            this.currentSlideIndex -= 1;
        },
        setActiveTab (tabIndex) {
            this.currentSlideIndex = tabIndex;
            clearInterval(this.timer)
            this.startSlider();
        }

    },
    components: {
        Slide,
        SlideNav
    },
    computed: {
        slide () {
            return this.slides[this.currentSlideIndex];
        }
    },
}
</script>

<style scoped>
.slider {
    position: relative;
}

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>