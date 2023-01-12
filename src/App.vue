<script >
import {store} from './store';
import axios from 'axios';

import AppCard from './components/AppCard.vue';
import AppSelect from './components/AppSelect.vue';
import AppLoader from './components/AppLoader.vue';

export default{
  components:{
    AppCard,
    AppSelect,
    AppLoader,
  },
  data(){
    return{
      store,
    }
  },
  methods:{
    getCardFromAPI(cardType){
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php', {
        params: {
          archetype: cardType,
          num: 10,
          offset: 0,
        }
      })
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
  <AppSelect  @changeTypeCard="getCardFromAPI(store.type)" />
  <h2>trovate {{ store.cardList.length }} carte</h2>
  <main class="vetrinaCard">
    <div v-if="store.cardList.length == 0">
      <AppLoader/>
    </div>
    <div class="singleCard" v-for="card in store.cardList" v-else>
      <AppCard :nameCard="card.name" :typeCard="card.type" :archTypeCard="card.archetype" :imgCard="card.card_images[0].image_url" />
    </div>
  </main>
</template>

<style scoped>

.vetrinaCard{
    display: flex;
    flex-wrap: wrap;

    justify-content: center;


  }

  .singleCard{
    width: calc(100% / 5);

    margin-bottom: 2rem;

    display: flex;
    flex-direction: column;
    align-items: center;
  }

  h2{
    text-align: center;
    margin: 0;    
  }
</style>
