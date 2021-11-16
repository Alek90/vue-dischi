<template>
    <div id="disc_list">

        <select v-model="choiceGenre" name="music_genre" id="music_genre">
            <option value="All">All</option>
            <option value="Rock">Rock</option>
            <option value="Pop">Pop</option>
            <option value="Jazz">Jazz</option>
            <option value="Metal">Metal</option>
        </select>


        <select v-model="choiceAuthor" name="author" id="author">
            <option value="All_artist">All artist</option>
            <option v-for="disc in discs" :value="disc.author" :key="disc.author">{{disc.author}}</option>
        </select>

        <div v-if="loading != true" class="discs row mx-4 gy-4 gx-5 justify-content-center">

            <div class="col-md-2 px-4" v-for="disc in showFilterDisc" :key="disc.title">

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

            choiceGenre: 'All',

            choiceAuthor: 'All_artist',

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

       /*  selectChoice() {
            console.log(this.choiceGenre);
        } */

    },

    computed: {
        /* showFilterGenre() {
            if(this.choiceGenre === "All") {
                return this.discs;
            }else {
                const filteredGenre = this.discs.filter((disc) => {
                    return disc.genre == this.choiceGenre;
                });
                return filteredGenre;
            }

        },

        showFilterAuthor() {
            if(this.choiceAuthor === "All_artist") {
                return this.discs;
            }else {
                const filteredAuthor = this.discs.filter((disc) => {
                    return disc.author == this.choiceAuthor;
                });
                return filteredAuthor;
            }
        }, */


        showFilterDisc() {
            if(this.choiceGenre === "All" && this.choiceAuthor === "All_artist") {
                return this.discs;

            }else if(this.choiceGenre !== "All") {
                const filteredGenre = this.discs.filter((disc) => {
                    return disc.genre == this.choiceGenre;
                });
                return filteredGenre;

            }else/*  if(this.choiceAuthor !== "All_artist") */ {
                const filteredAuthor = this.discs.filter((disc) => {
                    return disc.author == this.choiceAuthor;
                });
                return filteredAuthor;
            }
        }

    }
}
</script>

<style lang="scss">

</style>