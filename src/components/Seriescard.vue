<template>
  <div class="seriescard">
    <p>{{ serie.name }}</p>
    <img :src="getFlag(serie.original_language)" alt="" class="img-fluid" />
    <p>{{ serie.original_language }}</p>
    <p>{{ this.vote }}</p>
    <p>{{ posterUrl }}</p>
  </div>
</template>

<script>
export default {
  name: "Seriescard",
  props: ["serie", "posterBaseUri"],
  data() {
    return {
      language: this.serie.original_language,
      posterUrl: this.getPoster(),
      vote: this.getVote(),
    };
  },
  methods: {
    getFlag: (language) => require(`@/assets/images/${language}.png`),
    getPoster() {
      return (this.posterUrl = `${this.posterBaseUri}w342${this.serie.poster_path}`);
    },
    getVote() {
      const initialVote = this.serie.vote_average;
      console.log("iniziale", initialVote);
      const finalVote = Math.ceil(initialVote / 2);
      console.log("finale", finalVote);
      return finalVote;
    },
  },
};
</script>

<style>
.seriescard {
  color: aliceblue;
}
</style>