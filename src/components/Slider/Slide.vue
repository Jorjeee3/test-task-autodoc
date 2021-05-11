<template>
    <article class="slide" :style="{backgroundImage: `url(${slide.image})`}">
        <h1 class="slide-title" v-html="parseMarkdown(slide.title)" />
        <span class="slide-subtitle">{{slide.subtitle}}</span>
        <a class="front-brake-link" :href="slide.link.src">{{slide.link.title}}</a>
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
    methods: {
        parseMarkdown(markdownText) {
            const htmlText = markdownText
                .replace(/^### (.*$)/gim, '<h3>$1</h3>')
                .replace(/^## (.*$)/gim, '<h2>$1</h2>')
                .replace(/^# (.*$)/gim, '<h1>$1</h1>')
                .replace(/^> (.*$)/gim, '<blockquote>$1</blockquote>')
                .replace(/\*\*(.*)\*\*/gim, '<b>$1</b>')
                .replace(/\*(.*)\*/gim, '<i>$1</i>')
                .replace(/!\[(.*?)\]\((.*?)\)/gim, "<img alt='$1' src='$2' />")
                .replace(/\[(.*?)\]\((.*?)\)/gim, "<a href='$2'>$1</a>")
                .replace(/\n$/gim, '<br />')

            return htmlText.trim()
        }
    }
}
</script>

<style scoped>
.slide {
    height: 100vh;
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat;
    box-shadow: 70vw 0 50vw 0px rgba(255, 255, 255, 0.7) inset;
    padding: 100px 0 0 140px;
}

.slide-title {
    margin: 0;
    font-size: 70px;
    margin-bottom: 50px;
}

.slide-title ::v-deep b {
    color: red;
    font-weight: inherit;
}

.slide-subtitle {
    display: block;
    font-size: 20px;
    color: #000;
    margin-bottom: 30px;
}

.front-brake-link {
    text-decoration: none;
    color: rgb(201, 5, 5);
    padding-bottom: 5px;
    border-bottom: 2px solid rgb(201, 5, 5);
    display: inline-block;
}

</style>