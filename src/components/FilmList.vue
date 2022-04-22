<template>
  <div class="container">
    <div class="card" v-for="film in films" :key="film.id">
      <h2>{{ film.title }}</h2>
      <h4>({{ film.original_title }})</h4>
      <img
        v-if="flagAvailable.includes(film.original_language)"
        class="flag"
        :src="`./img/${film.original_language}.png`"
        :alt="film.original_language"
      />
      <span>{{ film.original_language }}</span>
      <p>{{ film.vote_average }}</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "FilmList",
  props: {
    films: Array,
  },
  data() {
    return {
      flagAvailable: ["en", "it", "cn", "es", "fr", "jp", "ru", "us"],
    };
  },
};
</script>

<style lang='scss' scoped>
.container {
  max-width: 1200px;
  margin: 50px auto;
  display: flex;
  flex-wrap: wrap;
  .card {
    width: 200px;
    height: 350px;
    display: flex;
    flex-direction: column;
    padding: 10px;
    border: 2px solid black;
    background-color: white;
    .flag {
      width: 20px;
    }
  }
}
</style>