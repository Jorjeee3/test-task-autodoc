<template>
    <div class="slider">
        <transition name="fade" mode="out-in" tag="div">
            <Slide :key="slide.title" :slide="slide" />
        </transition>
        
        <SlideNav
            :tabs="slides"
            :sliderStopped="stopped"
            :currentSlideIndex="currentSlideIndex"
            :autoStart="sliderOptions.autoStart"
            :animationDuration="sliderOptions.animationDuration"
            @set-active-tab="setActiveTab" 
            @start-slider="start"
            @stop-slider="stop"
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
            stopped: false
        };
    },
    props: {
        slides: {
            type: Array,
            required: true
        },
        sliderOptions: {
            type: Object,
            default() {
                return {
                    autoStart: true,
                    animationDuration: 5000,
                }
            },
        },
    },
    mounted () {
        this.start();
    },

    methods: {
        start () {
            if (this.sliderOptions.autoStart) {
                this.timer = setInterval(this.next, this.sliderOptions.animationDuration);
                this.stopped = false
            }
        },
        stop () {
            clearInterval(this.timer)
            this.stopped = true
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
            this.start();
        },

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

.fade-enter-active, .fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>