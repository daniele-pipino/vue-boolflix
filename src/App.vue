<template>
  <div id="app">
    <Header @findFilm="takeValue" />
    <Main :films="films" :series="series" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Main from "@/components/Main.vue";
export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      baseUri: "https://api.themoviedb.org/3",
      api_key: "ec0bc680bef001b261ae0afb63dfeaa0",
      query: "",
      films: [],
      series: [],
    };
  },
  methods: {
    takeValue(userResearch) {
      this.query = userResearch;
      this.getFilm();
      this.getSeries();
    },
    getFilm() {
      axios
        .get(
          `${this.baseUri}/search/movie?api_key=${this.api_key}&query=${this.query}`
        )
        .then((res) => {
          this.films = res.data.results;
          console.log(this.films);
        });
    },
    getSeries() {
      axios
        .get(
          `${this.baseUri}/search/tv?api_key=${this.api_key}&query=${this.query}`
        )
        .then((res) => {
          this.series = res.data.results;
          console.log(this.series);
        });
    },
  },
};
</script>

<style lang="scss">
@import "scss/style.scss";
</style>
