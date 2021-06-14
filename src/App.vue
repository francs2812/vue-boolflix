<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header />
  </div>
</template>

<script>
import Header from './components/Header.vue'
//import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    Header
    //HelloWorld
  }
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
      padding: 30px;
    }
</style>
