<template>
  <div class="container">
    <div class="card" v-for="series in series" :key="series.id">
      <h2>{{ series.name }}</h2>
      <h4>({{ series.original_name }})</h4>
      <img
        v-if="flagAvailable.includes(series.original_language)"
        class="flag"
        :src="`./img/${series.original_language}.png`"
        :alt="series.original_language"
      />
      <p>{{ series.original_language }}</p>
      <p>{{ series.vote_average }}</p>
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
  }
}
</style>