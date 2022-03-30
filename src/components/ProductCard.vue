<template>
  <div id="single-card">
    <div class="card mb-3" style="width: 18rem;">
      <img :src="character.poster" class="card-img-top p-3" alt="...">
      <div class="card-body">
        <h5 class="card-title">{{ character.title }}</h5>
        <p class="card-text">{{ character.author }}</p>
        <p class="card-text">{{ character.year }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'MusicCard',
  props: { 'character' : Object }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    @import '@/style/main-style.scss';
    #single-card{
      .card{
      background-color: $brand-color;
      }
    }
    
</style>
