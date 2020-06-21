<template lang="html">
  <div class="pkmnlistitem">
    <p>{{pkmn.name}}</p>
    <!-- <img :src='pkmn.sprites.front_default' :alt='pkmn.name'> -->
    <button v-on:click="displayInfo">Dex Entry</button>
    <button v-if="!pkmn.isInTeam" v-on:click="addToTeam"> Add to Team</button>
    <button v-if="pkmn.isInTeam" v-on:click="removeFromTeam">Remove from Team</button>
  </div>
</template>

<script>
import {eventBus} from "../main.js";
export default {
  name: "pkmn-list-item",
  props: ["pkmn"],
  methods: {
    displayInfo: function() {
      eventBus.$emit("pkmn-selected", this.pkmn);
    },
    addToTeam: function() {
      eventBus.$emit("pkmn-added", this.pkmn);
    },
    removeFromTeam: function () {
      eventBus.$emit("pkmn-removed", this.pkmn);
    }
  }
};
</script>

<style lang="css" scoped>
p {
  color: white
}
</style>
