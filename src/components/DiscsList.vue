<template>
    <div class="discs row mx-4 gy-4 gx-5 justify-content-center">

        <div class="col-md-2 px-4" v-for="disc in discs" :key="disc.title">

            <div class="disc p-4 text-center bg-secondary">

                <img :src="disc.poster" alt="disc.title 'cover'">

                <h5 class="text-white my-4">{{disc.title.toUpperCase()}}</h5>

                <div class="info">

                    <div class="author">{{disc.author}}</div>
                    <div class="year">{{disc.year}}</div>
                    
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

    .author{
        font-size: 1.2rem;
        line-height: 1.3rem;
    }

}

</style>