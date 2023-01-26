<script>
import AppMain from './components/AppMain.vue';
import { store } from './data/store';
import axios from 'axios';
import SearchBar from './components/SearchList.vue';
export default {
  data() {
    return {
      store,
      type: "",
      pokemonTypes: [
        "Ground",
        "Steel",
        "Fairy",
        "Fire",
        "Normal",
        "Dragon",
        "Dark",
        "Poison",
        "Electric",
        "Fighting",
        "Rock",
        "Ghost",
        "Psychic",
        "Grass",
        "Ice",
        "Bug",
        "Flying",
        "Water"
      ],
      apiUriType: "https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?per=20&eq[type1]="
    }
  },
  methods: {
    changeType(value) {
      store.pokemons = [""]
      this.type = value;
      this.apiUriType = `https://41tyokboji.execute-api.eu-central-1.amazonaws.com/dev/api/v1/pokemons?per=20&eq[type1]=${this.type}`
      axios.get(this.apiUriType).then(res => {
        store.pokemons = res.data.docs
        if (!this.type) {
          axios.get(store.apiUri).then(res => { store.pokemons = res.data.docs })
        }
      })
    },
    // resetArray() {
    //   store.pokemons = [""];
    // }
  },
  components: { AppMain, SearchBar },
};
</script>

<template>
  <div class="container my-5 box text-center p-5">
    <header class="text-center p-3">
      <figure class="mb-0">
        <img class="img-fluid"
          src="https://upload.wikimedia.org/wikipedia/commons/9/98/International_Pok%C3%A9mon_logo.svg" alt="">
      </figure>
      <SearchBar :options="pokemonTypes" @value-change="changeType" />
    </header>
    <AppMain />
  </div>

</template>

<style lang="scss">
figure {
  width: 100%;

  img {
    width: 50%;
  }
}

.box {
  height: auto;
  width: 100%;
  background-color: #dedede;
  border-radius: 1%;
  box-shadow: 10px 10px 10px 10px gold;
  border: 5px solid gold
}
</style>