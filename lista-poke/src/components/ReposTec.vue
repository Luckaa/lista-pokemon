<template>
<div  class="card " style="width: 16rem;">
  <img class="card-img-top" src="https://vignette.wikia.nocookie.net/victoryroad/images/e/ef/XYArt_Mega_Blastoise.png/revision/latest/scale-to-width-down/340?cb=20131011205623" alt="">
  <div class="card-body">
    <h5 href="" class="text-capitalize card-title">{{pokemon.name}}</h5>
    <p class="card-text">Nº{{pokemonAtual.id}}</p>
    <a href="#" class="btn btn-primary">{{pokemon.name}}</a>
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
