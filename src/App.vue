<template>
  <div id="app">
    <GeradorDeLink />
  </div>
</template>

<script>
import GeradorDeLink from "./components/GeradorDeLink.vue";

export default {
  name: "App",
  components: {
    GeradorDeLink,
  },
};
</script>

<style lang="scss">
@import "./assets/scss/_variables.scss";
@import "bootstrap/scss/bootstrap";
@import "./assets/scss/_bootswatch.scss";
</style>
