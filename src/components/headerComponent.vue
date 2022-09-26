<template>
  <header class="w-100 px-3 py-2">
    <div class="logo">
        <i class="logoImg fa-brands fa-spotify"></i>
    </div>
  </header>
</template>

<script>
export default {
    name: 'headerComponent'
}
</script>

<style lang="scss" scoped>
header{
    background-color: #2e3a46;

    .logoImg{
        font-size: 2rem;
        color: #1ed760
    }
}
</style>