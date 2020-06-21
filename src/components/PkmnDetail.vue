<template lang="html">
  <div id="detail">
  <div v-if="pkmn">
    <div id="detail-view">
      <h2>{{pkmn.name}}</h2>
      <div class="image">
        <img :src='pkmn.sprites.front_default' :alt='pkmn.name'>
        <img :src='pkmn.sprites.front_shiny' :alt='pkmn.name'>
      </div>
      <div class="property">
        <div class="left">Pokedex Number: </div>
        <div class="right">{{ pkmn.id }}</div>
      </div>
      <div class="property">
        <div class="left">Height: {{ pkmn.height / 10}} m</div>
        <div class="right">Weight: {{ pkmn.weight / 10}} kg</div>
      </div>
      <h3>Type</h3>
      <div class="types">
        <div class="type" v-for="(value, index) in pkmn.types" :key="'value'+index">
          {{ value.type.name }}
        </div>
      </div>
      <h3>Abilities</h3>
      <div class="abilities">
        <div class="ability" v-for="(value, index) in pkmn.abilities" :key="'value'+index">
          {{ value.ability.name }}
        </div>
      </div>
      <!-- <h3>Dex Entry</h3>
      <div class="">
        <div class="pokedex">{{getPkmnDex[0].flavour_text}}</div>
      </div> -->
      <!-- <button v-if="!pkmn.isInTeam" v-on:click="addToTeam">Add to Team</button>
      <button v-if="pkmn.isInTeam" v-on:click="removeFromTeam">Remove from Team</button> -->
    </div>
  </div>
</div>
</template>

<script>
// import {eventBus} from "../main.js";
export default {
  name: 'pkmn-detail',
  props: ['pkmn']
  // methods: {
  //   getDexEntry(pokemon) {
  //     const data = fetch(`${pokemon.species.url}`)
  //     const json = data.json()
  //     return json.flavor_text_entries.filter(function(element) {
  //       return element.language.name === 'en'
  //     })
  //   }
  //   addToTeam: function() {
  //     eventBus.$emit("pkmn-added", this.pkmn);
  //   },
  //   removeFromTeam: function () {
  //     eventBus.$emit("pkmn-removed", this.pkmn);
  //   }

}

</script>

<style lang="css" scoped>

#detail-view {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  position: inherit;
  width: 400px;
  height: 500px;
  max-width: 800px;
  padding: 10px 0 0;
  background: radial-gradient(lightgoldenrodyellow, yellow);
  border-radius: 5px;
  border-style: ridge;
  box-shadow: 0 15px 30px rgba(0,0,0,.2),
  0 10px 10px rgba(0,0,0,.2);
  top: 0   ;
  padding: 10px 10px 10px;

}
.image {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  top: -11px;
  width: 200px;
  height: 120px;
  background-color: white;
  border-style: ridge;
  border-radius: 5px;
  overflow: hidden;
  box-shadow: 0 5px 10px rgba(0,0,0,.2),
  0 10px 10px rgba(0,0,0,.2);
}

.data {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;
  width: 100%;
  margin-bottom: 40px;
}
.property {
  width: 90%;
  max-width: 400px;
  border-bottom: 1px solid #ccc;
  margin-bottom: 10px;
}
.left { float: left; }
.right { float: right; }


h3 {
  max-width: 400px;
  border-bottom: 1px solid #ccc;
}

.types, .abilities {
  display: flex;
  justify-content: flex-start;
  flex-wrap: wrap;
  width: 90%;
  max-width: 400px;
}
.type, .ability {
  margin: 0 10px 10px 0;
  padding: 5px 10px;
  border-radius: 20px;
  color: black;
  font-size: 1rem;
  letter-spacing: 2px;
}

.type { background-color: darkgrey; }
.ability { background-color: white; }

</style>
