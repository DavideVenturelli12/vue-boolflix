<template>
  <main>
    <FilmList :films="films" />
  </main>
</template>

<script>
import FilmList from "./FilmList.vue";

export default {
  name: "MainComponent",
  components: {
    FilmList,
  },
  props: {
    films: Array,
  },
};
</script>

<style lang="scss" scoped>
main {
  height: 100vh;
  display: flex;
  background-color: black;
  overflow: auto;
}
::-webkit-scrollbar {
  background: none;
}
</style>