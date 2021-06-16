<template>
  <div>
      <div v-if="arrayFilm.length != 0 ">
        <div
        v-for="(film, index) in arrayFilm" 
        :key="index" >
                <Card 
                :title="film.title" 
                :originalTitle="film.original_title"
                :originalLanguage="film.original_language"
                :voteAverage="film.vote_average"
                :poster="film.poster_path"
                :originalName="film.original_name"
                :name="film.name"
                :descrition="film.overview"
                />
        </div>
      </div>
       <h1 style="color: red; text-transform: uppercase" v-else>Non abbiamo trovato nulla che corrisponda alla tua ricerca</h1>
  </div>
</template>

<script>
import Card from './Card.vue';
export default {
  components: { Card },
    name:"Main",
    props : {
        "arrayFilm": Object
    },
    computed:{
        test: function() {
            let arrayFilms = this.arrayFilm

            //console.log(arrayFilms);
            return arrayFilms
        }
    },

    data: function() {
       return {
           arrayFilms: ""
       } 
    }
}
</script>

<style lang="scss" scoped>
        h1 {
            color: red;
            width: 60%;
            margin: 50px auto;
            text-align: center;
        }
</style>>
