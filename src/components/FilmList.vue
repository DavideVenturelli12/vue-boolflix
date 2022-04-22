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
      <p v-else class="flagNotAvaileble">{{ film.original_language }}</p>
      <p>{{ film.vote_average }}</p>
      <img
        v-if="film.poster_path != null"
        :src="'https://image.tmdb.org/t/p/w342' + film.poster_path"
        :alt="film.original_title"
      />
      <img
        v-else
        class="no-image"
        src="../assets/no-image.png"
        alt="not available"
      />
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
    .flagNotAvaileble {
      font-size: 20px;
      font-weight: 600;
    }
  }
}
</style>