<script>
import axios from 'axios';
import { store } from '../data/store'
export default {
    name: 'AppMain',
    data() {
        return {
            store,

        }
    },
    mounted() {
        axios.get(store.apiUri).then(res => { store.pokemons = res.data.docs })
    }
}     
</script>

<template>
    <h1 class=" text-danger" v-if="store.pokemons.length < 10">
        Loading...</h1>
    <div class="row mt-0">
        <div v-for="pokemon in store.pokemons" :key="pokemon.name" class="col-2 card-pokèmon text-center p-3 mb-3 mt-1">
            <img class="img-fluid" :src="pokemon.imageUrl" :alt="pokemon.name">
            <h4 class="mt-2  ">Name: {{ pokemon.name }}</h4>
            <h4 class="mt-2  ">Type: {{ pokemon.type1 }}</h4>
        </div>
    </div>
</template>

<style scoped lang="scss">
.row {
    width: 90%;
    margin: 0 auto;
}

.col-2 {
    width: calc(100% / 5);
    height: 400px;
}

img {
    width: 230px;
    height: 230px;
    object-fit: fill;
    border-radius: 20%;
    box-shadow: 0 0 10px blue;

}

// HOVER----
.card-pokèmon:hover {
    border: 5px solid gold;
    background-color: gold;
    transform: scale(1.1)
}
</style>