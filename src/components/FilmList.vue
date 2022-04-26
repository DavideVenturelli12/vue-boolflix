<template>
  <div class="container">
    <div class="card" v-for="film in films" :key="film.id">
      <!--card info-->
      <div class="info">
        <h3>
          TITOLO: <span>{{ film.title }}</span>
        </h3>
        <h3 v-if="film.title != film.original_title">
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
            <!--stelle piene-->
            <i
              :key="'star' + index"
              v-for="(star, index) in getStars(film)"
              class="fa-solid fa-star stars"
            >
            </i>
            <!--stelle vuote-->
            <i
              :key="'emptystar' + index"
              v-for="(emptystar, index) in 5 - getStars(film)"
              class="fa-regular fa-star"
            ></i>
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
        <h3>{{ film.title }}</h3>
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
  methods: {
    getStars(film) {
      return Math.ceil(film.vote_average / 2);
    },
  },
};
</script>

<style lang='scss' scoped>
@import "@/styles/item";
</style>