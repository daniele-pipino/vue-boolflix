<template>
  <main class="">
    <div class="container">
      <div class="row">
        <div class="col-4">
          <Filmcard v-for="(film, index) in films" :key="index" />
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
  height: 100vh;
  background-color: grey;
}
</style>