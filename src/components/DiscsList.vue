<template>
    <div class="discs row mx-4 gy-4 gx-5 justify-content-center">

        <div class="col-md-2 px-4" v-for="disc in discs" :key="disc.year">

            <div class="disc p-4 text-center bg-secondary">

                <img :src="disc.poster" alt="disc.title 'cover'">

                <h3 class="text-white my-4">{{disc.title}}</h3>

                <div class="info">

                    <div>{{disc.author}}</div>
                    <div>{{disc.year}}</div>
                    
                </div>

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

.disc{
    height: 100%;

    img{
        width: 100%;
    } 
}

</style>