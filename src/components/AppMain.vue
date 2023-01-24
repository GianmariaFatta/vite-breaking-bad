<script>
import axios from 'axios';
import { store } from '../data/store'
export default {
    name: 'AppMain',
    data() {
        return {
            store
        }
    },
    mounted() {
        axios.get(store.apiUri).then(res => { store.pokemons = res.data.docs })
    }
}     
</script>

<template>
    <div class="row">
        <!-- <h1 v-if="">Loading...</h1> -->
        <div v-for="pokemon in store.pokemons" :key="pokemon.name" class="col-2 text-center p-4">
            <img class="img-fluid" :src="pokemon.imageUrl" :alt="pokemon.name">
            <h4 class="mt-2  ">{{ pokemon.name }}</h4>
        </div>
    </div>
</template>

<style scoped lang="scss">
.col-2 {
    width: calc(100% / 5)
}

img {
    width: 230px;
    height: 230px;
    object-fit: fill;
    border-radius: 20%;
    box-shadow: 0 0 10px blue;

}
</style>