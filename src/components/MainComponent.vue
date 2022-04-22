<template>
  <main>
    <FilmList :films="films" />
    <SeriesList :series="series" />
  </main>
</template>

<script>
import FilmList from "./FilmList.vue";
import SeriesList from "./SeriesList.vue";

export default {
  name: "MainComponent",
  components: {
    FilmList,
    SeriesList,
  },
  props: {
    films: Array,
    series: Array,
  },
};
</script>

<style lang="scss" scoped>
main {
  height: 92vh;
  display: flex;
  flex-direction: column;
  background-color: black;
  overflow: auto;
}
::-webkit-scrollbar {
  width: 20px;
  background: rgb(52, 52, 52);
}

/* Handle */
::-webkit-scrollbar-thumb {
  background: rgb(67, 67, 67);
}

/* Handle on hover */
::-webkit-scrollbar-thumb:hover {
  background: rgb(83, 83, 83);
}
</style>