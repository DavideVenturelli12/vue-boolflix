<template>
  <div class="container">
    <div class="card" v-for="film in films" :key="film.id">
      <h2>{{ film.title }}</h2>
      <h4>({{ film.original_title }})</h4>
      <p>{{ film.original_language }}</p>
      <p>{{ film.vote_average }}</p>
    </div>
  </div>
</template>

<script>
/*

id
title
original_title
original_language
vote_average

*/
export default {
  name: "FilmList",
  props: {
    films: Array,
  },
};
</script>

<style lang='scss' scoped>
.container {
  max-width: 1200px;
  margin: 100px auto;
  display: flex;
  flex-wrap: wrap;
  .card {
    width: 200px;
    height: 350px;
    display: flex;
    flex-direction: column;
    padding: 10px;
    border: 2px solid black;
    border-radius: 10px;
    background-color: white;
  }
}
</style>