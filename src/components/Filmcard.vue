<template>
  <div class="filmcard">
    <p>{{ film.title }}</p>
    <img
      v-if="flags.includes(film.original_language)"
      :src="getFlag(film.original_language)"
      alt=""
      class="img-fluid"
    />
    <p class="m-1" v-else>{{ film.original_language }}</p>
    <p class="d-flex justify-content-center my-3">
      <i v-for="(value, name) in this.vote" :key="name" class="fas fa-star"></i>
      <i
        v-for="(value, index) in this.totalStar - this.vote"
        :key="index"
        class="far fa-star"
      ></i>
    </p>
    <!-- <p class="copertina">{{ posterUrl }}</p> -->
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
      totalStar: 5,
      flags: ["en", "it"],
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
};
</script>

<style lang="scss">
.filmcard {
  color: aliceblue;
  img {
    height: 20px;
  }
  i {
    color: gold;
  }
}
</style>