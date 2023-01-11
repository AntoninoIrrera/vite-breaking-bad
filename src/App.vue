<script >
import {store} from './store';
import axios from 'axios';

import AppCard from './components/AppCard.vue'

export default{
  components:{
    AppCard,
  },
  data(){
    return{
      store,
    }
  },
  methods:{
    getCardFromAPI(){
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=12&offset=0')
        .then((response) => {
          console.log(response.data.data);

          store.cardList = response.data.data;
        })
        
    }
  },
  created(){
    this.getCardFromAPI();
  }
}
</script>

<template>
  <h2>trovate {{ store.cardList.length }} carte</h2>
  <main class="vetrinaCard">
    <div class="singleCard" v-for="card in store.cardList">
      <AppCard :nameCard="card.name" :typeCard="card.type" :imgCard="card.card_images[0].image_url" />
    </div>
  </main>
</template>

<style scoped>
.vetrinaCard{
    display: flex;
    flex-wrap: wrap;

    padding: 5rem;

  }

  .singleCard{
    width: calc(100% / 3 - 10px);


    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h2{
    margin-top: 2rem;
    text-align: center;
  }
</style>
