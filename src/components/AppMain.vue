<script>
import axios from 'axios';
export default {
    name: 'AppMain',
    data() {
        return {
            pokemons: []
        }
    },
    mounted() {
        axios.get('https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?per=10&page=8').then(res => { this.pokemons = res.data.docs })
    }
}     
</script>

<template>
    <div class="row">
        <!-- <h1 v-if="">Loading...</h1> -->
        <div v-for="pokemon in pokemons" :key="pokemon.name" class="col-2 text-center p-4">
            <img class="img-fluid" :src="pokemon.imageUrl" :alt="pokemon.name">
            <h5>{{ pokemon.name }}</h5>
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
}
</style>