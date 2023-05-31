<template>
  <div class="pokemon-container">
    <img :src="imgsrc" 
    class="hidden-pokemon"
    alt="pokemon">
    <img v-if="verPokemon" 
      :src="imgsrc" 
      class="fade-in"
      alt="pokemon">
  </div>
 
</template>

<script>
export default {
      props:{
        pokeid:{
         type: Number,
          required:true,
        },
        verPokemon:{
          type:Boolean,
          required:true,
          default:false
        }
      },
      computed:{
        imgsrc(){
          return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${this.pokeid}.svg`
        }
      }
}
</script>

<style scoped>
/* Pokemon Picture */
.pokemon-container {
    height: 200px;
}
img {
  height: 200px;
  position: absolute;
  width: 100vw;
  margin-left: -50vw;
  user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  -webkit-user-drag: none;
  -webkit-user-select: none;
}
.hidden-pokemon {
    filter: brightness(0);
}

</style>