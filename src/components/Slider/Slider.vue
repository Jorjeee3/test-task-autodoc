<template>
    <div class="slider">

    </div>
</template>

<script>
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