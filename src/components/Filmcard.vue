<template>
  <div class="filmcard">
    <p>{{ film.title }}</p>
    <p>{{ film.original_title }}</p>
    <p>{{ film.original_language }}</p>
    <p>{{ film.vote_average }}</p>
  </div>
</template>

<script>
export default {
  name: "Filmcard",
  props: ["film"],
};
</script>

<style>
.filmcard {
  color: aliceblue;
}
</style>