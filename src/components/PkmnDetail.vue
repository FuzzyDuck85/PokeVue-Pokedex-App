<template lang="html">
  <div v-if="pkmn">
    <div>
      <h3>{{pkmn.name}}</h3>
      <div>
        <img :src='pkmn.sprites.front_default' :alt='pkmn.name'>
        <img :src='pkmn.sprites.front_shiny' :alt='pkmn.name'>
      </div>
      <div class="dex">
        <div>Pokedex Number: {{ pkmn.id }}</div>
      </div>
      <br>
      <div class="types">Type:
        <div class="type" v-for="(value, index) in pkmn.types" :key="'value'+index">
          {{ value.type.name }}
        </div>
      </div>
      <br>
      <div class="size">
        <div>Height: {{ pkmn.height / 10}} m</div>
        <div>Weight: {{ pkmn.weight / 10}} kg</div>
      </div>
    </div>
    <br>
    <div class="description">Abilities:
      <div class="ability" v-for="(value, index) in pkmn.abilities" :key="'value'+index">
        {{ value.ability.name }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'pkmn-detail',
  props: ['pkmn']
}

</script>

<style lang="css" scoped>
body {
  text-transform: capitalize;
}
</style>
