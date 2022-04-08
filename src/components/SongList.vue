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
import axios from "axios";

export default {
  name: "SongList",
  components: {
    SongItem,
  },
  data() {
    return {
      allSong: [],
    };
  },
  mounted() {
    this.generateCard();
  },
  methods: {
    generateCard() {
      axios
        .get("https://flynn.boolean.careers/exercises/api/array/music")
        .then((response) => {
          const song = response.data;
          for (let i = 0; i < song.response.length; i++) {
            this.allSong.push(song.response[i]);
          }

          console.log(this.allSong);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";

main {
  width: 70%;
  margin: auto;
  padding: 80px 0;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>