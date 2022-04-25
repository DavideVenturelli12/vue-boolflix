<template>
  <div class="container">
    <div class="card" v-for="film in films" :key="film.id">
      <!--card info-->
      <div>
        <h3>
          TITOLO: <span>{{ film.title }}</span>
        </h3>
        <h3>
          TITOLO ORIGINALE:
          <span>
            {{ film.original_title }}
          </span>
        </h3>
        <img
          v-if="flagAvailable.includes(film.original_language)"
          class="flag"
          :src="`./img/${film.original_language}.png`"
          :alt="film.original_language"
        />
        <p v-else class="flagNotAvaileble">
          LINGUA: {{ film.original_language }}
        </p>
        <h3>
          VOTO:
          <span>
            {{ film.vote_average / 2 }}
          </span>
        </h3>
        <h3 v-if="film.overview != ''">
          OVERVIEW: <span>{{ film.overview }}</span>
        </h3>
        <h3 v-else>OVERVIEW: <span>non disponibile </span></h3>
      </div>

      <!--card poster-->
      <img
        v-if="film.poster_path != null"
        class="poster"
        :src="'https://image.tmdb.org/t/p/w342' + film.poster_path"
        :alt="film.original_title"
      />
      <div v-else class="no-image">
        <p>ANTEPRIMA NON DISPONIBILE</p>
      </div>
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
@import "@/styles/item";
</style>