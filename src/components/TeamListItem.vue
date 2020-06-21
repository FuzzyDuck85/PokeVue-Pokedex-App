<template lang="html">
  <li>
    {{ pkmn.name }}
    <button v-on:click="selectedPkmn">Dex Entry</button>
    <button v-on:click="removeFromTeam">Remove from Team</button>
  </li>
</template>

<script>
import { eventBus } from "../main.js"
export default {
  props: ["pkmn"],
  methods: {
    selectedPkmn: function(){
      eventBus.$emit("pkmn-selected", this.pkmn);
    },
    removeFromTeam: function(){
      eventBus.$emit("pkmn-removed", this.pkmn);
    }
  }
}
</script>

<style lang="css" scoped>
</style>
