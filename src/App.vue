<template lang="">
  <div id="app" class="main">
    <img src="../public/pokevuetransparent.png" alt="PokéVue"><br>
    <pkmn-filter-form :pokemon="pokemon" /><br>
    <div>
      <pkmn-detail v-if="selectedPkmn" :pkmn="selectedPkmn"></pkmn-detail>
      <!-- <pkmn-list :pokemon="pokemon"></pkmn-list> -->
      <!-- <team-list :team="team"></team-list> -->
      <!-- <pkmn-select :pokemon="pokemon"></pkmn-select> -->
    </div><br>
    <p>By Donald Cameron</p>

  </div>
</template>

<script>
import {eventBus} from './main.js'
// import PkmnList from './components/PkmnList.vue'
// import PkmnSelect from './components/PkmnSelect.vue'
import PkmnDetail from './components/PkmnDetail.vue'
// import TeamList from '.components/TeamList.vue'
import PkmnFilterForm from './components/PkmnFilterForm.vue'
export default {
  name: 'App',

  data(){
    return{
      pokemon:[],
      selectedPkmn: null
    }
  },
  methods: {
    getPokemon: function() {
      fetch(`https://pokeapi.co/api/v2/pokemon?limit=807/`)
        .then(res => res.json())
        .then(data => this.pokemon = data.results)
      },
      getDexEntry: function() {
        fetch(`https://pokeapi.co/api/v2/pokemon-species?limit=807/`)
          .then(res => res.json())
          .then(data => this.pokemon = data.results)
        }
      },
      mounted(){
        this.getPokemon();
        eventBus.$on('pkmn-selected', (pkmn) => {
          fetch (`${pkmn.url}`)
          .then(res => res.json())
          .then(data => this.selectedPkmn = data)
        })
      },
      components: {
        'pkmn-filter-form' :PkmnFilterForm,
        // 'pkmn-select' :PkmnSelect,
        'pkmn-detail' :PkmnDetail
        // 'team-list' :TeamList
        // 'pkmn-list'   :PkmnList
        // },
        // computed: {
        //   team: function() {
        //     return this.pokemon.filter(pkmn => pkmn.isInTeam);
        //   }
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
    p{
      color: darkred}
      </style>
