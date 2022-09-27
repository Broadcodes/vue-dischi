<template>
  <div class="card">
    <img :src="cd.poster" :alt="cd.author" @error="replaceWrongImageUrl" />
    <h2>{{ cd.title }}</h2>
    <h3>{{ cd.author }}</h3>
    <h3>{{ cd.year }}</h3>
  </div>
</template>

<script>
import errorImage from "@/assets/img/bon-jovi-new-jersey.jpg";

export default {
  methods: {
    replaceWrongImageUrl(e) {
      e.target.src = errorImage;
    },
  },
  props: {
    // Recuper i dati da mainContainerCards.vue
    cd: Object,
  },
};
</script>

<style lang="scss" scoped>
.card {
  height: 100%;
  padding: 20px;
  background-color: rgba(204, 204, 204, 0.07);

  img {
    width: 100%;
  }

  h2 {
    color: #fff;
    font-size: 1rem;
    text-transform: uppercase;
    text-align: center;
    padding: 10px;
  }

  h3 {
    color: rgba(255, 255, 255, 0.3);
    font-size: 0.8rem;
    text-align: center;
    padding: 1px;
  }
}
</style>