<template>
  <div class="container">
    <div class="card" v-for="serie in series" :key="serie.id">
      <h2>{{ serie.name }}</h2>
      <h4>({{ serie.original_name }})</h4>
      <img
        v-if="flagAvailable.includes(serie.original_language)"
        class="flag"
        :src="`./img/${serie.original_language}.png`"
        :alt="serie.original_language"
      />
      <p v-else class="flagNotAvaileble">{{ serie.original_language }}</p>
      <p>{{ serie.vote_average }}</p>
      <img
        v-if="serie.poster_path != null"
        :src="'https://image.tmdb.org/t/p/w342' + serie.poster_path"
        :alt="serie.original_name"
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
  name: "SereisList",
  props: {
    series: Array,
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
    background-color: white;
    .flag {
      width: 20px;
    }
    .flagNotAvaileble {
      font-size: 20px;
      font-weight: 600;
    }
    .no-image {
      width: 100px;
      margin: 50px auto;
    }
  }
}
</style>