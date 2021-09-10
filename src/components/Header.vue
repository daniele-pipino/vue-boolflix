<template>
  <header class="bg-dark d-flex align-items-center justify-content-between">
    <h1 class="text-center mx-5">BOOLFLIX</h1>
    <input
      type="text"
      class="form-control w-25 mx-5"
      placeholder="Cerca il tuo film..."
      aria-label="Username"
      aria-describedby="basic-addon1"
    />
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style lang="scss">
header {
  height: 70px;
  color: red;
}
</style>