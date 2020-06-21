<template lang="">
  <div id="app">
    <p>PokeDex</p>
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
    fetch(`https://pokeapi.co/api/v2/pokemon?limit=151/`)
      .then(res => res.json())
      .then(data => this.pokemon = data.results)

      eventBus.$on('pkmn-selected', (pkmn) => {
        fetch (`${pkmn.url}`)
        .then(res => res.json())
        .then(data => this.selectedPkmn = data)
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
    text-transform: capitalize;
    font-family: 'Press Start 2P';
    line-height: 160%;
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
