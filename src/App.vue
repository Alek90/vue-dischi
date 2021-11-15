<template>
  <div id="app">
    <HeaderSite />
    <MainSite />
  </div>
</template>

<script>
//import axios from 'axios';
import HeaderSite from './components/HeaderSite.vue';
import MainSite from './components/MainSite.vue'

export default {
  name: 'App',
  components: {
    HeaderSite,
    MainSite
  },

  
}
</script>

<style lang="scss">

/* importazione bootstrap */
@import "../node_modules/bootstrap/scss/bootstrap.scss";
@import "./assets/scss/style.scss";
@import url('https://fonts.googleapis.com/css2?family=Lato:wght@400;700&display=swap');


</style>
