<template>
  <div id="index-main">
    <select id="music-genere" v-model="genere">
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
    <button class="btn btn-primary" @click="musicalGenre()">Console Genere</button>
    <div class="my-container p-5">
      <div class=" d-flex flex-wrap justify-content-evenly">
        <div v-for="(element, index) in mainCards" :key="index" >
          <ProductCard 
          :character="element"
          v-if="genere == element.genre"
          />
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
      genere: ''
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
    },
    musicalGenre(){
      for(let i = 0; i < this.mainCards.length; i++){
        console.log(this.mainCards[i].genre);
        
      }
      console.warn(this.genere);
    },
    selecteCard(element){
      if(this.genere == ''){
        this.genere = element.genre;
      }
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
