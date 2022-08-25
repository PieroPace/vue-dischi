<template>
  <div class="col p-1 mt-3 text-center">
    <img class="img-fluid mb-1 p-3" :src="album.poster" :alt="album.title" />
    <h1 class="fs-5 text-white text-uppercase">
      {{ album.title }}
    </h1>
    <h2 class="fs-6">
      {{ album.author }}
    </h2>
    <h3 class="fs-6">
      {{ album.year }}
    </h3>
  </div>
</template>

<script>
export default {
  name: "Album",
  props: ["album"],
};
</script>

<style scoped lang="scss">
.col {
  background-color: #2e3a46;
  h2,
  h3 {
    color: grey;
  }
}
</style>
