<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->

  <!-- (v-bind o :) se utiliza para mandar una expresionde javascript -->
  <!-- <Counter title="Calculo" :start="15"/> -->
  <Indecision />
</template>

<script>
// import Counter from './components/Counter.vue';
import Indecision from './components/Indecision.vue';


export default {
    name: "App",
    components: { 
      // Counter, 
      Indecision 
    }
}
</script>

<style>
html{
  background-color: #2c3e50;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
