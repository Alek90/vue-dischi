<template>
    <div id="disc_list">

        <div v-if="loading != true" class="discs row mx-4 gy-4 gx-5 justify-content-center">

            <div class="col-md-2 px-4" v-for="disc in showFilterDiscs" :key="disc.title">

                <div class="disc p-4 text-center">

                    <img :src="disc.poster" alt="disc.title 'cover'">

                    <h5 class="text-white my-4">{{disc.title.toUpperCase()}}</h5>

                    <div class="info">

                        <div class="author">{{disc.author}}</div>
                        <div class="year">{{disc.year}}</div>
                        
                    </div>

                </div>

            </div>

        </div>

        <div v-if="loading != false">

            <h2 class="text-center text-white">
                LOADING...
            </h2>

        </div>

         <select v-model="choiceGenre" @change="selectChoice()" name="music_genre" id="music_genre">
            <option value="all">All</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>

        <!-- quando cambio valore del select, devo filtrare i disc che contengono genre = value. -->


    </div>

</template>

<script>
import axios from 'axios';

export default {

    name: 'DiscsList',

    data(){
        return{
            discs: {},

            choiceGenre: 'all',

            loading: true
        }
    },

    mounted() {

        setTimeout(this.callAPI, 3000);
        
    },

    methods: {
        callAPI() {
            axios
            .get('https://flynn.boolean.careers/exercises/api/array/music')
            .then(r => {
            //console.log(r.data);
            this.discs = r.data.response;
            this.loading = false;
            }).catch(e => {
            console.log(e);
            });
        },

        selectChoice() {
            console.log(this.choiceGenre);
        }

    },

    computed: {
        showFilterDiscs() {
            if(this.choiceGenre === "all"){
                console.log('ciao');
                return this.discs;
            }

                const filteredDiscs = this.discs.filter((disc) => {
                    return disc.genre == this.choiceGenre
                });
                console.log(filteredDiscs, this.choiceGenre);
                return filteredDiscs;
        }
    }

    
}
</script>

<style lang="scss">

</style>