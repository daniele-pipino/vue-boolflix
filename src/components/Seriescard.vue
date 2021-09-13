<template>
  <div class="seriescard">
    <p>{{ serie.name }}</p>
    <img
      v-if="flags.includes(serie.original_language)"
      :src="getFlag(serie.original_language)"
      alt=""
      class="img-fluid"
    />
    <p v-else>{{ serie.original_language }}</p>
    <p class="d-flex justify-content-center my-3">
      <i v-for="(value, name) in this.vote" :key="name" class="fas fa-star"></i>
      <i
        v-for="(value, index) in this.totalStar - this.vote"
        :key="index"
        class="far fa-star"
      ></i>
    </p>
    <!-- <p>{{ posterUrl }}</p> -->
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
      flags: ["it", "en"],
      totalStar: 5,
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

<style lang="scss">
.seriescard {
  color: aliceblue;
  img {
    height: 20px;
  }
  i {
    color: gold;
  }
}
</style>