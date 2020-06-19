<template lang="html">
  <div v-if="pkmn">
    <h3>{{pkmn.name}}</h3>
    <div v-if="pokemon" class="image">
        <img :src="imageUrl + pokemon.id + '.png'" alt="">
      </div>
    <ul>

    </ul>
  </div>
</template>

<script>
export default {
  name: 'pkmn-detail',
  props: ['pkmn']
}
</script>

<style lang="css" scoped>
</style>
