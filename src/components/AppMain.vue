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
    <h1 class=" text-danger" v-if="store.pokemons.length < 5">
        Loading...</h1>
    <div class="row mt-0">
        <div v-for="pokemon in store.pokemons" :key="pokemon.name"
            class="col-2 card-pokèmon  text-center p-3 mb-3 mt-1">
            <img class="img-fluid" :class="pokemon.type1" :src="pokemon.imageUrl" :alt="pokemon.name">
            <h4 class="mt-2">Name: {{ pokemon.name }}</h4>
            <h4 class="mt-2 ">Type: {{ pokemon.type1 }}</h4>
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

    // box-shadow: 0 0 10px blue;


}



// HOVER----
.card-pokèmon:hover {
    border: 5px solid gold;
    background-color: gold;
    transform: scale(1.1)
}

// TYPE COLOR - - - -
.Grass {
    box-shadow: 0 0 30px green;
}

.Ground {
    box-shadow: 0 0 30px brown;
}

.Steel {
    box-shadow: 0 0 30px lightsteelblue;
}

.Fairy {
    box-shadow: 0 0 30px pink;
}

.Fire {
    box-shadow: 0 0 30px darkred;
}

.Normal {
    box-shadow: 0 0 30px bisque;
}

.Dragon {
    box-shadow: 0 0 30px orange;
}

.Dark {
    box-shadow: 0 0 30px black;
}

.Poison {
    box-shadow: 0 0 30px purple;
}

.Electric {
    box-shadow: 0 0 30px gold;
}

.Fighting {
    box-shadow: 0 0 30px grey;
}

.Rock {
    box-shadow: 0 0 30px lightslategrey;
}

.Ghost {
    box-shadow: 0 0 30px palevioletred;
}

.Psychic {
    box-shadow: 0 0 30px yellowgreen;
}

.Ice {
    box-shadow: 0 0 30px lightblue;
}

.Bug {
    box-shadow: 0 0 30px #D898B2;
}

.Flying {
    box-shadow: 0 0 30px #7094AE;
}

.Water {
    box-shadow: 0 0 30px blue;
}
</style>