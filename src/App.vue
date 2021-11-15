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

  /* mounted(){

    axios
    .get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(r => {
      console.log(r);
    }).catch(e => {
      console.log(e);
    })
  } */
}
</script>

<style lang="scss">

/* importazione bootstrap */
@import "../node_modules/bootstrap/scss/bootstrap.scss";


</style>
