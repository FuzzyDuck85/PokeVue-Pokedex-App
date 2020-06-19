<template lang="html">
  <div>
    <select v-on:change="handleSelect" v-model="selectedPkmn">
      <option v-for="(pkmn, index) in pokemon.results" :value="pkmn" :key="index">{{pkmn.name}}</option>
    </select>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
  name: 'pkmn-select',
  props: ['pokemon'],
  data(){
    return{
      "selectedPkmn": null
    }
  },
  methods: {
    handleSelect(){
      eventBus.$emit('pkmn-selected', this.selectedPkmn)
    }
  }
}
</script>

<style lang="css" scoped>
</style>
