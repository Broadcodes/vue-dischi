<template>
  <div class="card">
    <img :src="cd.poster" :alt="cd.author">
    <h2>{{cd.title}}</h2>
    <h3>{{cd.author}}</h3>
    <h3>{{cd.year}}</h3>
  </div>
</template>

<script>
export default {
    props: {
    cd: Object,
  },
}
</script>

<style lang="scss" scoped>
    .card{
        height: 100%;
        padding: 20px;
        background-color: rgba(255, 255, 255, 0.1);

        img{
            width: 100%;
        }

        h2{
          color: #fff;
          font-size: 1rem;  
          text-transform: uppercase;
          text-align: center;
          padding: 10px;
        }

        h3{
            color: rgba(255, 255, 255, 0.3);
          font-size: 0.8rem;  
          text-align: center;
          padding: 1px;
        }
    }
</style>