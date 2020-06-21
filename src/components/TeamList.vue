<template lang="html">
  <div id="team-list">
    <ul>
      <team-list-item v-for="(pkmn, index) in team" :pkmn="pkmn" :key="index" ></team-list-item>
    </ul>
  </div>
</template>

<script>
import TeamListItem from "./components/TeamListItem.vue";
export default {
  name: "team-list",
  props: ["team"],
  components: {
    "team-list-item": TeamListItem
  }
}
</script>

<style lang="css" scoped>
</style>
