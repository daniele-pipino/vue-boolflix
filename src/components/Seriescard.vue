<template>
  <div class="seriescard p-3 m-2">
    <p>{{ serie.name }}</p>
    <img
      v-if="flags.includes(serie.original_language)"
      :src="getFlag(serie.original_language)"
      alt=""
      class="img-fluid flag-image"
    />
    <p v-else>{{ serie.original_language }}</p>
    <p class="d-flex justify-content-center my-3 align-items-center">
      Voto:
      <span
        ><i v-for="(value, id) in this.vote" :key="id" class="fas fa-star"></i
      ></span>
      <span
        ><i
          v-for="(value, id, name) in this.totalStar - this.vote"
          :key="name"
          class="far fa-star"
        ></i
      ></span>
    </p>
    <p>{{ serie.overview }}</p>
    <div class="seriescard-cover">
      <img :src="`${this.posterBaseUri}w342${serie.poster_path}`" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  name: "Seriescard",
  props: ["serie", "posterBaseUri"],
  data() {
    return {
      language: this.serie.original_language,
      vote: this.getVote(),
      flags: ["it", "en"],
      totalStar: 5,
    };
  },
  methods: {
    getFlag: (language) => require(`@/assets/images/${language}.png`),
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
  .seriescard-cover {
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