<template>
  <div class="gs-card">
    <img class="img-fluid" :src="Img" :alt="Author" />
    <h5>{{ Title }}</h5>
    <p>{{ Author }}</p>
    <p>{{ Year }}</p>
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

@media screen and (max-width: 1460px) {
  h5,
  p {
    font-size: 0.8rem;
  }
}
.gs-card {
  text-align: center;
  background-color: $bg-card;
  padding: 20px 15px;
  width: 200px;
  margin: 10px 20px;
  h5 {
    color: $title-color;
    margin-top: 10px;
    text-transform: uppercase;
    font-weight: bold;
    padding: 0px 5px;
  }
  p {
    color: $description-color;
    margin: 0;
  }
}
</style>