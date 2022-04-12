<template>
  <main>
    <!-- SELECT OPTION FILTER SONG BY GENRE -->
    <select @change="selectedLabel($event)">
      <option value="">All</option>
      <option v-for="genere in uniqueGenre()" :key="genere" :value="genere">
        {{ genere }}
      </option>
    </select>
    <!-- ALL SONG CARDS -->
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
    <!-- LOADING CARDS -->
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
    // GENERATE CARD FROM API
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
    //GET VALUE OF SHOWGENRE BY SELECTED LABEL
    selectedLabel(event) {
      this.showGenre = event.target.value;
    },
    // GET NEW ARRAY FILTERED TO GENERATE CARDS FILTERED
    filteredSongByGenre() {
      return this.allSong.filter((element) =>
        element.genre.includes(this.showGenre)
      );
    },
    //GET UNIQUE GENRE ON OPTIONS
    uniqueGenre() {
      const uniqueGenre = [];
      for (let i = 0; i < this.allSong.length; i++) {
        if (!uniqueGenre.includes(this.allSong[i].genre)) {
          uniqueGenre.push(this.allSong[i].genre);
        }
      }
      return uniqueGenre;
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