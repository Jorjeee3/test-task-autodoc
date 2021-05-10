<template>
    <article class="slide" :style="{backgroundImage: `url(${slide.image})`}">
        
    </article>
</template>

<script>
export default {
    props: {
        slide:{
            type: Object,
            required: true,
        }
    }, 
}
</script>

<style scoped>

</style>