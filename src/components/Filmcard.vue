<template>
  <div class="filmcard">
    <p>{{ film.title }}</p>
    <img :src="`@/assets/images/${this.language}.png`" alt="" />
    <p>{{ film.original_language }}</p>
    <p>{{ film.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Filmcard",
  props: ["film"],
  data() {
    return {
      language: this.film.original_language,
    };
  },
  created() {
    console.log(this.language);
  },
};
</script>

<style lang="scss">
.filmcard {
  color: aliceblue;
  img {
    height: 20px;
  }
}
</style>