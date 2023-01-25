<script>
import AppMain from './components/AppMain.vue';
import axios from 'axios';
import { store } from './data/store';
import SearchBar from './components/SearchList.vue';
export default {
  data() {
    return {
      store,
      pokemonTypes: ["Ground",
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
        "Water"]
    }
  },
  mounted() {
    axios.get(store.apiUri_Types).then(res => { store.pokèmonTypes = res.data })
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
      <SearchBar @value-change="" />
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