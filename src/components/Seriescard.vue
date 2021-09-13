<template>
  <div class="seriescard">
    <p>{{ serie.name }}</p>
    <img :src="this.getFlag" alt="" />
    <p>{{ serie.original_language }}</p>
    <p>{{ serie.vote_average }}</p>
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
    };
  },
  methods: {
    getFlag: (language) => require(`@/assets/images/${language}.png`),
    getPoster() {
      return (this.posterUrl = `${this.posterBaseUri}w342${this.serie.poster_path}`);
    },
  },
};
</script>

<style>
.seriescard {
  color: aliceblue;
}
</style>