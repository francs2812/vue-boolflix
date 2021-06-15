<template>
  <div>
      <div v-for="(film, index) in arrayFilm" :key="index">
            <Card 
            :title="film.title" 
            :originalTitle="film.original_title"
            :originalLanguage="film.original_language"
            :voteAverage="film.vote_average"
            />
      </div>
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

            console.log(arrayFilms);
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

<style>

</style>