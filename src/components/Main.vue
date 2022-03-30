<template>
  <div id="index-main">
    <div class="my-container p-5">
      <div class=" d-flex flex-wrap justify-content-evenly">
        <div v-for="(element, index) in mainCards" :key="index">
          <ProductCard :character="element"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
import ProductCard from './ProductCard.vue'
export default {
  name: 'IndexMain',
  components:{
    ProductCard
  },
  data: function(){
    return{
      mainCards: null,
    }
  },
  created: function(){
    this.getApiInfo();
  },
  methods: {
    getApiInfo(){
      axios
      .get('https://flynn.boolean.careers/exercises/api/array/music')
      .then((result) =>{
        this.mainCards = result.data.response;
        console.log(this.mainCards);
      })
      .catch((error) => {
        console.error(error);
      })
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
  @import '@/style/main-style.scss';
  #index-main{
    background-color: #1E2D3B;
    .my-container{
      width: 90%;
      margin: 0 auto;
    }
  }
</style>
