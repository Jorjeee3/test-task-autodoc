<template>
  <div id="app">
    <Index />
    
  </div>
</template>

<script>
import Index from "./pages/Index.vue";

export default {
  name: "app",
  components: {
    Index
  }
};
</script>

<style>
@import './styles/normalize.css';
@import './styles/typography.css';

</style>
