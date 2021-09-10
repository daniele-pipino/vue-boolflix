<template>
  <main class="">
    <div class="container mx-auto">
      <div class="row">
        <div
          class="col-4 text-center my-3 border"
          v-for="(film, index) in films"
          :key="index"
        >
          <Filmcard :film="film" />
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import Filmcard from "@/components/Filmcard.vue";
export default {
  name: "Main",
  props: ["films"],
  components: {
    Filmcard,
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