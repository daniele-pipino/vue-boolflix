<template>
  <main class="">
    <div class="container mx-auto">
      <h1 class="text-center">FILM</h1>
      <!-- start film  -->
      <div class="row g-3">
        <div
          class="col-4 text-center my-3"
          v-for="(film, index) in films"
          :key="index"
        >
          <Filmcard :film="film" :posterBaseUri="posterBaseUri" />
        </div>
      </div>
      <!-- end film -->
      <h1 class="text-center">SERIES</h1>
      <!--start series-->
      <div class="row">
        <div
          class="col-4 text-center my-3"
          v-for="(serie, index) in series"
          :key="index"
        >
          <Seriescard :serie="serie" :posterBaseUri="posterBaseUri" />
        </div>
      </div>
      <!-- end series -->
    </div>
  </main>
</template>

<script>
import Filmcard from "@/components/Filmcard.vue";
import Seriescard from "@/components/Seriescard.vue";
export default {
  name: "Main",
  props: ["films", "series"],
  components: {
    Filmcard,
    Seriescard,
  },
  data() {
    return {
      posterBaseUri: " https://image.tmdb.org/t/p/",
    };
  },
  methods: {},
  created() {
    console.log(this.films);
  },
};
</script>

<style lang="scss">
main {
  min-height: 100vh;
  background-color: grey;
}
</style>