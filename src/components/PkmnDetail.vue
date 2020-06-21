<template lang="html">
  <div v-if="pkmn">
    <div class="detail-view">
      <h2>{{pkmn.name}}</h2>
      <div>
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
.detail {
  display: flex;
  justify-content: center;
  align-items: flex-start;
  position: fixed;
  top: 0;
  left: 0;
  padding: 90px 10px 10px;
  width: calc(100% - 20px);
  height: calc(100vh - 20px);
  background: rgba(color: #000000, alpha: .7);
}
.detail-view {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  position: relative;
  width: 100%;
  max-width: 800px;
  padding: 10px 0 0;
  background: radial-gradient(white, lightblue);
  border-radius: 5px;
  box-shadow: 0 15px 30px rgba(0,0,0,.2),
  0 10px 10px rgba(0,0,0,.2);
  top: 0   ;
  padding: 10px 10px 10px;

}
.image {
  display: flex;
  justify-content: center;
  align-items: center;
  position: absolute;
  top: -60px;
  width: 120px;
  height: 120px;
  background-color: #333;
  border-radius: 50%;
  overflow: hidden;
  box-shadow: 0 15px 30px rgba(0,0,0,.2),
  0 10px 10px rgba(0,0,0,.2);
}

h2 {
  text-transform: capitalize;
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
  width: 90%;
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
  text-transform: capitalize;
  word-wrap: none;
  word-break: keep-all;
}

.type { background-color: darkgrey; }
.ability { background-color: white; }

.close {
  outline: none;
  border: none;
  border-radius: 5px;
  background-color: #333;
  color: #efefef;
  padding: 10px 20px;
  margin-bottom: 20px;
  font-size: 1.2rem;
  cursor: pointer;
}

i {
  font-size: 2rem;
  color: #efefef;
}
</style>
