<template>
  <h1 v-if="!pokemon">Espere porfavor</h1>
  <div v-else>
    <h1>¿Quien es este pokemon?</h1>
    <!-- picture -->
    <PokemonPicture :pokeid="pokemon.id" :verPokemon="showpokemon"></PokemonPicture>

    <!-- opciones -->
    <PokemonOptions :pokemons="pokemonArr"></PokemonOptions>
  </div>
</template>

<script>
import PokemonOptions from '@/components/PokemonOptions.vue'
import PokemonPicture from '@/components/PokemonPicture.vue'

import getPokemonOptions from '@/helpers/getPokemonOptions'

//console.log(getPokemonOptions());

export default {
    components:{
        PokemonOptions,
        PokemonPicture
    },
   data(){
    return{
      pokemonArr:[],
      pokemon:null,
      showpokemon:false
    }
   },
   methods:{
     async mixPokemonArray(){
        this.pokemonArr=await getPokemonOptions()
        const rndInt = Math.floor(Math.random()*4)
        this.pokemon=this.pokemonArr[rndInt]
       // console.log(this.pokemonArr)
      }
   },
   mounted(){
    this.mixPokemonArray()
   }

}
</script>

