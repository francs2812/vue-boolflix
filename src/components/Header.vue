<template>
  <div class="d-flex justify-content-around align-items-center"> 
    <a href="https://fontmeme.com/netflix-font/"><img src="https://fontmeme.com/permalink/210614/dbe2da256cf873b5e39378a2ee64c904.png" alt="netflix-font" border="0"></a>
    <div>
        <input @keyup="movieSearch" v-model="serch" type="text">
        <input @click="$emit(`prova`, trasferArrayFilm)" type="button" value="search">
    </div>

    <!-- <div>
        <h1 v-for="(film, index) in films" :key="index">
            {{film.title}}
            {{film.original_title}}
            {{film.original_language}}
        </h1>
    </div> -->
  </div>
</template>

<script>
import axios from "axios";

export default {
    name: 'Header',
    data: function(){
        return {
              serch:"",
              url:"https://api.themoviedb.org/3/search/movie" , 
              films:""
        }
    },
    methods:{
       movieSearch() {
            axios.get(this.url ,{ 
                    params:{
                      api_key : "021c1d61b0a3435190dbf0a9fc20b605",
                      language : "it-IT",
                      query : this.serch,
                    }
            })
            .then( 
                (response) => {
                    //console.log(response);
                    this.films = response.data.results;
                    //console.log( this.film);
            })
            }
    },
    computed: {
        trasferArrayFilm: function() {
            const ArrayFilm = this.films;
            return ArrayFilm;
        }
    }

}
</script>

<style lang="scss" scoped>


</style>