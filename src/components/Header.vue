<template>
  <div class="d-flex justify-content-around align-items-center"> 
    <a href="/home"><img src="https://fontmeme.com/permalink/210614/dbe2da256cf873b5e39378a2ee64c904.png" alt="netflix-font" border="0"></a>
    <div>
        <input @keyup="movieSearch" @keydown="seriesTvSearch" v-model="serch" type="text">
        <input @click="$emit(`prova`, trasferArrayFilm)" type="button" value="search">
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
    name: 'Header',
    data: function(){
        return {
              serch:"",
              urlFilm:"https://api.themoviedb.org/3/search/movie" , 
              urlserieTv:"https://api.themoviedb.org/3/search/tv" , 
              films:"",
              serieTv:""
        }
    },
    methods:{
       movieSearch() {
            axios.get(this.urlFilm ,{ 
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
            },
        seriesTvSearch() {
            axios.get(this.urlserieTv ,{ 
                    params:{
                      api_key : "021c1d61b0a3435190dbf0a9fc20b605",
                      language : "it-IT",
                      query : this.serch,
                    }
            })
            .then( 
                (response) => {
                    //console.log(response);
                    this.serieTv = response.data.results;
                    console.log( this.response.data.results);
            })
        }
    },
    computed: {
        trasferArrayFilm: function() {
            const ArrayFilmTv = this.films.concat(this.serieTv);
            return ArrayFilmTv;
        }
    }

}
</script>

<style lang="scss" scoped>


</style>