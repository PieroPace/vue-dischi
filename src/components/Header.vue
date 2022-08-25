<template>
  <header class="container-fluid mb-5">
    <div class="row">
      <div class="col-1">
        <img class="logo" src="../assets/logo.png" alt="Logo" />
      </div>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header",
};
</script>

<style scoped lang="scss">
.row {
  background-color: #2e3a46;
  .logo {
      width: 50%;
      padding: 0.5em;
  }
}
</style>
