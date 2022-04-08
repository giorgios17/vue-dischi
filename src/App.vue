<template>
  <div id="app">
    <HeaderComponent />
    <SongList />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import SongList from "./components/SongList.vue";

export default {
  name: "App",
  components: {
    HeaderComponent,
    SongList,
  },
};
</script>

<style lang="scss">
@import "@/assets/style/reset";
@import "~bootstrap";
@import "@/assets/style/variables";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background-color: $bg-main;
  height: 100vh;
}
</style>
