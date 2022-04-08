<template>
  <div>
    <SongItem />
  </div>
</template>

<script>
import SongItem from "@/components/SongItem.vue";

export default {
  name: "SongList",
  components: {
    SongItem,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";
</style>