<template>
    <div class="discs row justify-content-center">

        <div class="disc card text-center col-md-2 bg-secondary" v-for="disc in discs" :key="disc.year">

            <img :src="disc.poster" alt="disc.title 'cover'">

            <h2 class="text-white">{{disc.title}}</h2>

            <div class="info">

                <p>{{disc.author}}</p>
                <p>{{disc.year}}</p>
                
            </div>

        </div>

    </div>
</template>

<script>
import axios from 'axios';


export default {

    name: 'DiscsList',

    data(){
        return{
            discs: {}
        }
    },

    mounted() {

        axios
        .get('https://flynn.boolean.careers/exercises/api/array/music')
        .then(r => {
        console.log(r.data);
        this.discs = r.data.response;
        console.log(this.discs);
        }).catch(e => {
        console.log(e);
    })
    }
}
</script>

<style lang="scss">

</style>