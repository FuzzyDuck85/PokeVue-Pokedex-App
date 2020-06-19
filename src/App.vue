<template lang="">
  <div id="app">
    <p>Pokemon Select</p>
    <pkmn-select :pokemon="pokemon"></pkmn-select>
    <pkmn-detail :pkmn="selectedPkmn"></pkmn-detail>

  </div>
</template>

<script>
import {eventBus} from './main.js'
import PkmnSelect from './components/PkmnSelect.vue'
import PkmnDetail from './components/PkmnDetail'
export default {
  name: 'App',
  data(){
    return{
      pokemon:[],
      selectedPkmn: null
    }
  },
  mounted(){
    fetch('https://pokeapi.co/api/v2/pokemon?limit=151')
    .then(res => res.json())
    .then(data => this.pokemon = data)

    eventBus.$on('pkmn-selected', (pkmn) => {
      this.selectedPkmn = pkmn
    })
  },
  components: {
    'pkmn-select' :PkmnSelect,
    'pkmn-detail' :PkmnDetail
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

@import url('https://use.fontawesome.com/releases/v5.8.2/css/all.css');

body {
  margin: 0;
  padding: 0;
}
</style>
