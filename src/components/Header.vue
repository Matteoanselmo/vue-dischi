<template>
  <div id="index-header">
    <img src="../img/spotify-logo.png" alt="spotify logo">
  </div>
</template>

<script>
export default {
  name: 'IndexHeader'
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '@/style/main-style.scss';
  #index-header{
    background-color: $brand-color;
    height: 10vh;
  }
</style>
