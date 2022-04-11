<template>
  <main>
    <select @change="selectedLabel($event)">
      <option value="">All</option>
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
    <div
      v-if="allSong.length > 0"
      class="container d-flex flex-wrap justify-content-center"
    >
      <SongItem
        :key="index"
        v-for="(song, index) in filteredSongByGenre()"
        :Img="song.poster"
        :Title="song.title"
        :Author="song.author"
        :Year="song.year"
      />
    </div>
    <div v-else>
      <LoadingComponent />
    </div>
  </main>
</template>
<script>
import SongItem from "@/components/SongItem.vue";
import LoadingComponent from "@/components/LoadingComponent.vue";
import axios from "axios";

export default {
  name: "SongList",
  components: {
    SongItem,
    LoadingComponent,
  },
  data() {
    return {
      allSong: [],
      showGenre: "",
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
        });
    },
    selectedLabel(event) {
      this.showGenre = event.target.value;
    },
    filteredSongByGenre() {
      return this.allSong.filter((element) =>
        element.genre.includes(this.showGenre)
      );
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
}
</style>