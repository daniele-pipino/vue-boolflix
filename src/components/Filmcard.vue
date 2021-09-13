<template>
  <div class="filmcard">
    <p>{{ film.title }}</p>
    <img :src="`@/assets/images/${this.language}.png`" alt="" />
    <p>{{ film.original_language }}</p>
    <p>{{ film.vote_average }}</p>
    <p class="copertina">{{ posterUrl }}</p>
  </div>
</template>

<script>
export default {
  name: "Filmcard",
  props: ["film", "posterBaseUri"],
  data() {
    return {
      language: this.film.original_language,
      posterUrl: this.getPoster(),
    };
  },
  methods: {
    getPoster() {
      return (this.posterUrl = `${this.posterBaseUri}w342${this.film.poster_path}`);
    },
  },
  created() {},
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