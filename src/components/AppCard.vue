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
       archTypeCard: String,
   }
}
</script>

<template>

    <img :src="imgCard" :alt="nameCard">
    <h3>Name: {{ nameCard }}</h3>
    <h3>Type: {{ typeCard }}</h3>
    <h3>ArchType: {{ archTypeCard }}</h3>

</template>

<style scoped>
    img{
        width: 60%;
    }
    h3{
        margin: 0;
    }

   
</style>
