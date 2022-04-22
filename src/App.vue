<template>
  <div id="app">
    <HeaderComponent @search="searching" />
    <MainComponent :films="films" :series="series" />
  </div>
</template>

<script>
import HeaderComponent from "./components/HeaderComponent.vue";
import MainComponent from "./components/MainComponent.vue";

import axios from "axios";

export default {
  name: "App",
  components: {
    HeaderComponent,
    MainComponent,
  },
  data() {
    return {
      apiUrl: "https://api.themoviedb.org/3/search/",
      apiKey: "089652cdebc3953b09d9f6ae1f72abf9",
      films: [],
      series: [],
    };
  },
  methods: {
    searching(textToSearch) {
      //console.log("searched Text:", textToSearch);
      const paramsObj = {
        params: {
          api_key: this.apiKey,
          query: textToSearch,
          language: "it-IT",
        },
      };
      axios
        .get(this.apiUrl + "movie", paramsObj)
        .then((response) => {
          //console.log(response);
          if (response.status === 200) {
            this.films = response.data.results;
          }
        })
        .catch((error) => console.log(error));

      axios.get(this.apiUrl + "tv", paramsObj).then((response) => {
        //console.log(response);
        if (response.status === 200) {
          this.series = response.data.results;
        }
      });
    },
  },
};
</script>

<style lang="scss">
@import "@/styles/general";
</style>
