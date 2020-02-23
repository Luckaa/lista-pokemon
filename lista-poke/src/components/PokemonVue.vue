<template>
<div v-if="pokemonAtual.sprites.front_default !== null"  class="card border-dark mb-1 ml-1" style="width: 16rem;">
  <img class="card-img-top"  :src="pokemonAtual.sprites.front_default" alt="sprite do pokemon da api">
  <div class="card-body">
    <h3 class="text-capitalize card-title">{{pokemon.name}}</h3>
    <h6 class="card-text">Nº{{pokemonAtual.id}}</h6>
    <div class="row">
    <h5><span  class="badge badge-pill badge-danger text-capitalize">{{pokemonAtual.types[0].type.name}}</span></h5>
    <h5><span  v-if="pokemonAtual.types.length > 1" class="badge badge-pill badge-secondary text-capitalize">{{pokemonAtual.types[1].type.name}}</span></h5>
    </div>
  </div>
</div>




</template>
<script>

import axios from "axios";



export default {
    props:["pokemon"],
   mounted() {
     this.getPokeAtual();
  },
  data(){
    return{
      pokeapi:{
        urlPoke:"https://pokeapi.co/api/v2/pokemon",
      },
      pokemonAtual:"",
    }
  },

  methods:{
    

   
  getPokeAtual(){
      let pokemonAtual = this.pokemonAtual
      const {urlPoke} = this.pokeapi
      let teste1 = this.pokemon.name
      axios.get(`${urlPoke}/${teste1}`).then(({data})=> this.pokemonAtual = data)
  },
  

  }
  }


</script>
