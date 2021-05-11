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

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: #2c3e50;
}

</style>
