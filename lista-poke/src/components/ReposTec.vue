<template>
<div class="card" style="width: 23rem;">
  <img class="card-img-top" src="https://assets.pokemon.com/assets/cms2/img/pokedex/full/009.png" alt="">
  <div class="card-body">
    <h5 href="" class="card-title">{{pokemon.name}}</h5>
    <p class="card-text">{{pokemon.name}}</p>
    <a href="#" class="btn btn-primary">{{pokemon.name}}</a>
  </div>
</div>



</template>
<script>

const API_URL = "http://localhost:3000/"
import axios from "axios";
export default {
    props:["pokemon"]
    ,
  
    
}
</script>