<template>
  <div class="load">
    <i class="imgLoading fa-solid fa-circle-notch"></i>
    <h2>LOADING...</h2>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss" scoped>
.load {
  width: 100%;
  height: calc(100vh - 56px);
  background-color: #1e2d3b;
  display: flex;
  justify-content: center;
  align-items: center;

  .imgLoading {
    font-size: 5rem;
    color: rgb(18, 128, 158);
    position: relative;
    animation: load 1.5s infinite linear;
  }

  @keyframes load {
    0% {
      transform: rotate(0deg);
    }
    100% {
      transform: rotate(360deg);
    }
  }

  h2 {
    padding-left: 40px;
    color: #fff;
    position: relative;
    animation: colorText 10s infinite linear;
  }

  @keyframes colorText {
    0% {
        color: #fff;
    }
    50% {
        color: rgb(18, 128, 158);
    }
    100% {
        color: #fff;
    }
  }
}
</style>