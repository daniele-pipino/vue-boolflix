<template>
  <div class="filmcard p-3 m-1">
    <h4>Titolo: {{ film.title }}</h4>
    <img
      v-if="flags.includes(film.original_language)"
      :src="getFlag(film.original_language)"
      alt=""
      class="img-fluid flag-image"
    />
    <p class="m-1" v-else>Lingua:{{ film.original_language }}</p>
    <p class="d-flex justify-content-center my-3 align-items-center">
      Voto:
      <i v-for="(value, name) in this.vote" :key="name" class="fas fa-star"></i>
      <i
        v-for="(value, index) in this.totalStar - this.vote"
        :key="index"
        class="far fa-star"
      ></i>
    </p>
    <p>{{ film.overview || "No overview available" }}</p>
    <div class="filmcard-cover">
      <img :src="this.posterUrl" alt="" />
    </div>
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
  min-height: 500px;
  position: relative;
  display: block;
  cursor: pointer;
  background: #000;
  .flag-image {
    width: 30px;
  }
  i {
    color: gold;
  }
  .filmcard-cover {
    display: block;
    img {
      width: 100%;
      height: 100%;
      position: absolute;
      top: 0;
      left: 0;
    }
    &:hover {
      display: none;
    }
  }
}
</style>