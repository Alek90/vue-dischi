<template>
  <div id="app">
    <HeaderSite />
  </div>
</template>

<script>
import axios from 'axios';
import HeaderSite from './components/HeaderSite.vue'

export default {
  name: 'App',
  components: {
    HeaderSite,
  },

  mounted(){

    axios
    .get('https://flynn.boolean.careers/exercises/api/array/music')
    .then(r => {
      console.log(r);
    }).catch(e => {
      console.log(e);
    })
  }
}
</script>

<style lang="scss">

/* importazione bootstrap */
@import "../node_modules/bootstrap/scss/bootstrap.scss";


</style>
