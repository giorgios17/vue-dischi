<template>
  <div>
    <div class="gs-card">
      <img :src="Img" :alt="Author" />
      <h3>{{ Title }}</h3>
      <p>{{ Author }}</p>
      <p>{{ Year }}</p>
    </div>
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

export default {
  name: "SongItem",
  props: {
    Song: Array,
    Img: String,
    Title: String,
    Author: String,
    Year: String,
  },
};
</script>

<style lang="scss" scoped>
@import "@/assets/style/variables";
.gs-card {
  text-align: center;
  background-color: $bg-card;
  padding: 20px 15px;
  width: 200px;
  min-height: 340px;
  margin: 10px 20px;
  h3 {
    color: $title-color;
    margin-top: 10px;
    text-transform: uppercase;
    font-size: 20px;
    font-weight: bold;
  }
  p {
    color: $description-color;
    margin: 0;
  }
  img {
    width: 150px;
  }
}
</style>