<template>
  <div class="container">
    <div class="card" v-for="serie in series" :key="serie.id">
      <!--card info-->
      <div class="info">
        <h3>
          TITOLO:
          <span>
            {{ serie.name }}
          </span>
        </h3>
        <h3>
          TITOLO ORIGINALE:
          <span>
            {{ serie.original_name }}
          </span>
        </h3>
        <img
          v-if="flagAvailable.includes(serie.original_language)"
          class="flag"
          :src="`./img/${serie.original_language}.png`"
          :alt="serie.original_language"
        />
        <p v-else class="flagNotAvaileble">
          LINGUA: {{ serie.original_language }}
        </p>
        <h3>
          VOTO:
          <span>
            <!--stelle piene-->
            <i
              :key="'star' + index"
              v-for="(star, index) in getStars(serie)"
              class="fa-solid fa-star stars"
            >
            </i>
            <!--stelle vuote-->
            <i
              :key="'emptystar' + index"
              v-for="(emptystar, index) in 5 - getStars(serie)"
              class="fa-regular fa-star"
            ></i>
          </span>
        </h3>
        <h3 v-if="serie.overview != ''">
          OVERVIEW: <span>{{ serie.overview }}</span>
        </h3>
        <h3 v-else>OVERVIEW: <span>non disponibile </span></h3>
      </div>

      <!--card poster-->
      <img
        v-if="serie.poster_path != null"
        class="poster"
        :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path"
        :alt="serie.original_name"
      />
      <div v-else class="no-image">
        <h3>{{ serie.name }}</h3>
        <p>ANTEPRIMA NON DISPONIBILE</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SereisList",
  props: {
    series: Array,
  },
  data() {
    return {
      flagAvailable: ["en", "it", "cn", "es", "fr", "jp", "ru", "us"],
    };
  },
  methods: {
    getStars(serie) {
      return Math.ceil(serie.vote_average / 2);
    },
  },
};
</script>

<style lang='scss' scoped>
@import "@/styles/item";
</style>