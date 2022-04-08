<template>
  <main>
    <SongItem
      :key="index"
      v-for="(song, index) in allSong"
      :Img="song.poster"
      :Title="song.title"
      :Author="song.author"
      :Year="song.year"
    />
  </main>
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
main {
  background-color: $bg-main;
  padding: 50px;
  display: flex;
}
</style>