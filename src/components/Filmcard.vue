<template>
  <div class="filmcard">
    <p>{{ film.title }}</p>
    <img :src="getFlag(film.original_language)" alt="" class="img-fluid" />
    <p>{{ film.original_language }}</p>
    <p>{{ this.vote }}</p>
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
      vote: this.getVote(),
    };
  },
  methods: {
    getFlag(lang) {
      return require(`@/assets/images/${lang}.png`);
    },
    getPoster() {
      return (this.posterUrl = `${this.posterBaseUri}w342${this.film.poster_path}`);
    },
    getVote() {
      const initialVote = this.film.vote_average;
      console.log("iniziale", initialVote);
      const finalVote = Math.ceil(initialVote / 2);
      console.log("finale", finalVote);
      return finalVote;
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