<template lang="">
  <div id="app" class="main">
    <h1>PokeDex</h1>
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
    fetch(`https://pokeapi.co/api/v2/pokemon?limit=251/`)
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
  }
    h1 { color: #efefef; }
  .main {
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      padding: 10px;
      width: calc(100% - 20px);
      min-height: calc(100vh - 20px);
      background: radial-gradient(red, black);

      font-family: 'Acme', arial;
      font-size: 1rem;
      font-weight: normal;
    }
  </style>
