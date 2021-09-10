<template>
  <div id="app">
    <Header />
    <Main />
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
      query: "ciao",
      films: [],
    };
  },
  methods: {},
  created() {
    axios
      .get(
        `${this.baseUri}/search/movie?api_key=${this.api_key}&query=${this.query}`
      )
      .then((res) => {
        const result = res.data.results;
        console.log(result);
      });
  },
};
</script>

<style lang="scss">
@import "scss/style.scss";
body {
  background-color: rgb(44, 43, 43);
}
</style>
