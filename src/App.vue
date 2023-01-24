<script>
import AppMain from './components/AppMain.vue';
export default {

  components: { AppMain }
};
</script>

<template>
  <div class="container my-5 box text-center p-3">
    <img src="https://upload.wikimedia.org/wikipedia/commons/9/98/International_Pok%C3%A9mon_logo.svg" alt="">
    <header class="text-center p-5">
    </header>
    <AppMain />
  </div>

</template>

<style lang="scss">
.box {
  height: 1000px;
  width: 100%;
  background-color: #dedede;
}
</style>