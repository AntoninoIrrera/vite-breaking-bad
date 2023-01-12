<script >
import { store } from '../store';


export default {
    data() {
        return {
            store,
        }
    }
}
</script>

<template>

    <div>
        
        <select v-model="store.type" name="archType" id="archType" @change="$emit(`changeTypeCard`)">
            <option value="Alien">Alien</option>
            <option value="Laval">Laval</option>
            <option value="Vylon">Vylon</option>
            <option value="Inzektor">Inzektor</option>
            <option value="Umi">Umi</option>
            <option value="Gusto">Gusto</option>
        </select>
    
    </div>

</template>

<style scoped>
    div{
        text-align: center;
    }
</style>
