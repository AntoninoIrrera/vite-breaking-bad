<script >
import { store } from '../store.js'

export default {
   data(){
    return{
        store,
    }
   },
   props:{
       nameCard: String,
       typeCard: String,
       imgCard: null,
   }
}
</script>

<template>

    <img :src="imgCard" :alt="nameCard">
    <h3>{{ nameCard }}</h3>
    <h3>{{ typeCard }}</h3>



</template>

<style scoped>
    img{
        width: 50%;
    }

   
</style>
