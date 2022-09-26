<template>
  <div class="containerCards">
    <!-- Ciclo l'array recuperato da mainComponent.vue e passo i restanti dati a mainCard.vue -->
    <div class="cards" v-for="(item, index) in itemAlbum" :key="index">
      <mainCard :cd="item"/>
    </div>
  </div>
</template>

<script>
import mainCard from "./mainCard.vue";

export default {
  props: {
    // Recupero i dati dal mainComponent.vue
    itemAlbum: Array,
  },
  components: {
    mainCard,
  },
};
</script>

<style lang="scss" scoped>
.containerCards{
  max-width: 1000px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;

  .cards{
    width: calc(100% / 5 - 30px);
    margin: 9px 15px;
  }
}
</style>