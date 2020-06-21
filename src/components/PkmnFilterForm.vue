<template lang="html">
  <form v-on:submit.prevent>
    <input type="text" v-model="search" placeholder="type a pokémon name" v-on:keyup="searchForPkmn">
    <select v-on:change="handleSelect" v-model="selectedPkmn">
      <option disabled value="">Select a pokémon...</option>
      <option v-for="(pkmn, index) in pokemon" :value="pkmn" :key="index">{{pkmn.name}}</option>
    </select>
  </form>
</template>

<script>
import { eventBus } from '../main.js'
export default {
  name: "pkmn-filter-form",
  data(){
    return {
      "search" : "",
      "selectedPkmn": {},
    }
  },
  props: ["pokemon"],
  methods: {
    searchForPkmn(){
      let foundPkmn = this.pokemon.find((pkmn) => {
        return pkmn.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1
      })
      this.selectedPkmn = foundPkmn

      eventBus.$emit('pkmn-selected', this.selectedPkmn)
    },
    handleSelect(){
      this.search = ""
      eventBus.$emit('pkmn-selected', this.selectedPkmn)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
