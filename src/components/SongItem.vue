<template>
  <div class="card">
    <img :src="allSong.poster" :alt="allSong.author" />
    <h3>{{ allSong.title }}</h3>
    <p>{{ allSong.author }}</p>
    <p>{{ allSong.year }}</p>
  </div>
</template>

<script>
/* STRUTTURA BRANO CHIAMATO DA API
author: "Bon Jovi"
genre: "Rock"
poster: "https://www.onstageweb.com/wp-content/uploads/2018/09/bon-jovi-new-jersey.jpg"
title: "New Jersey"
year: "1988"
*/
import axios from "axios";

export default {
  name: "SongItem",
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
          this.allSong.push(response.data.response);
          console.table(this.allSong);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "~bootstrap";
</style>