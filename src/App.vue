<template>
  <div id="app">
    <Header />
    <Main />
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
#app {
  height: 100vh;
  background-color: #1e2d3b;
}
</style>
