<template>
    <div class="slider">
        <transition name="fade" tag="div">
            <Slide :key="slide.title" :slide="slide" />
        </transition>
        <SlideTab :tabs="slides" :currentSlideIndex="currentSlideIndex"/>
    </div>
</template>

<script>
import Slide from '@/components/Slider/Slide.vue';
import SlideTab from '@/components/Slider/SlideTab.vue'; 

export default {
    name: "slider",
    data() {
        return {
            timer: null,
            currentSlideIndex: 0
        };
    },
    props: {
        slides: {
            type: Array,
            required: true
        },
    },
    mounted () {
        this.startSlider ();
    },

    methods: {
        startSlider () {
            this.timer = setInterval(this.next, 2500);
        },

        next () {
            if (this.currentSlideIndex === this.slides.length - 1) {
                this.currentSlideIndex = 0
            } else {
                // this.currentSlideIndex += 1
            }
        },
        prev () {
            this.currentSlideIndex -= 1;
        }
    },
    components: {
        Slide,
        SlideTab
    },
    computed: {
        slide () {
            return this.slides[this.currentSlideIndex];
        }
    },
}
</script>

<style scoped>

</style>