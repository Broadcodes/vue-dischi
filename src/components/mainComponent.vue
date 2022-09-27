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
//   recupero i dati da app.vue
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
  height: calc(100vh - 55px);
}
</style>