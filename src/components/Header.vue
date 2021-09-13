<template>
  <header class="bg-dark d-flex align-items-center justify-content-between">
    <h1 class="text-center mx-3">BOOLFLIX</h1>
    <div class="d-flex mx-2">
      <input
        type="text"
        class="form-control"
        placeholder="Cerca il tuo film..."
        aria-label="Username"
        aria-describedby="basic-addon1"
        v-model="searchedFilm"
      />
      <button
        @click="$emit('findFilm', searchedFilm)"
        class="w-25 btn btn-light mx-3"
      >
        Cerca
      </button>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      searchedFilm: "",
    };
  },
};
</script>

<style lang="scss">
header {
  height: 70px;
  color: red;
}
</style>