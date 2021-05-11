<template>
    <div class="slider">
        <Slide />
    </div>
</template>

<script>
import Slide from '@/components/Slider/Slide.vue';

export default {
    name: "slider",
    data() {
        return {
            timer: null,
            currentSlideIndex: 0
        };
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
                this.currentSlideIndex += 1
            }
        },
        prev () {
            this.currentSlideIndex -= 1;
        }
    },
    components: {
        Slide
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