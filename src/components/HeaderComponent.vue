<template>
  <header>
    <img :src="logo" :alt="logo" />
  </header>
</template>

<script>
import logo from "@/assets/spotify-logo.png";

export default {
  name: "HeaderComponent",
  data() {
    return {
      logo: logo,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";
header {
  background-color: $bg-header;
  padding: 10px;
  display: flex;
  justify-content: flex-start;
  img {
    width: 50px;
  }
}
</style>