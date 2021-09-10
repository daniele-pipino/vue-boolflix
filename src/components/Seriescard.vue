<template>
  <div class="seriescard">
    <p>{{ serie.name }}</p>
    <img :src="`@/assets/images/${this.language}.png`" alt="" />
    <p>{{ serie.original_language }}</p>
    <p>{{ serie.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Seriescard",
  props: ["serie"],
  data() {
    return {
      language: this.serie.original_language,
    };
  },
};
</script>

<style>
.seriescard {
  color: aliceblue;
}
</style>