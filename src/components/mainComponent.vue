<template>
  <main>
    <MainCard :itemAlbum="album" />
  </main>
</template>

<script>
import MainCard from "./mainContainerCards.vue";
export default {
  components: {
    MainCard,
  },
  props: {
    album: Array,
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: #1e2d3b;
  display: flex;
  align-items: center;
  height: calc(100vh - 56px);
}
</style>