<template>
  <div id="app">
    <Header @prova="film" />
    <Main :arrayFilm = "film2" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Main from './components/Main.vue';
export default {
  name: 'App',
  data: function(){
    return{
      film2:""
    }
  },
  components: {
    Header,
    Main
  },
  methods: {
    film: function(filmSearch){
       let array = [];
      filmSearch.forEach(
        (element) => {
          array.push(element);
          //console.log(this.film2);
        return array ; 
      })
      //return this.film2 = this.prova;
      this.film2 = array;
   }

    //ritorno al futuro
  },
}
</script>

<style lang="scss">

  @import "./components/style/General";

  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    }

    body {
        background-color: #222222;
    }

</style>
