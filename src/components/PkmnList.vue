<template lang="html">
  <div class="pkmn-list" v-if="pokemon.length">
    <pkmn-list-item v-for="(pkmn, index) in pokemon" :pkmn="pkmn" :key="index"></pkmn-list-item>
  </div>
</template>

<script>
import PkmnListItem from "@/components/PkmnListItem.vue";

export default {
  name: "pkmn-list",
  props: ["pokemon"],
  components: {
    "pkmn-list-item": PkmnListItem
  }
};
</script>

<style lang="css" scoped>
</style>
