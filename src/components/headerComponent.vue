<template>
  <header>
    <i class="logoImg fa-brands fa-spotify"></i>
  </header>
</template>

<script>
export default {
  name: "headerComponent",
};
</script>

<style lang="scss" scoped>
header {
  background-color: #2e3a46;
  padding: 12px;

  .logoImg {
    padding-left: 10px;
    font-size: 2rem;
    color: #1ed760;
  }
}
</style>