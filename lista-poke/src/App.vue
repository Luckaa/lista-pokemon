
<template>
  <div  class="container" id="app">
        
    <div> 
      <nav>
        <ul class="pagination justify-content-center">
    <li v-if="this.pokeapi.offset>0" @click="anteriorpagPoke" class="page-item">
      <a class="page-link" href="#">Anterior</a>
    </li>
    <li @click="pag0" class="page-item"><a href="#" class="page-link">1</a></li>
    <li @click="pag1" class="page-item"><a href="#" class="page-link">2</a></li>
    <li @click="pag2" class="page-item"><a href="#" class="page-link">3</a></li>
    <li @click="pag3" class="page-item"><a href="#" class="page-link">4</a></li>
    <li @click="pag4" class="page-item"><a href="#" class="page-link">5</a></li>
    <li @click="pag5" class="page-item"><a href="#" class="page-link">6</a></li>
    <li @click="pag6" class="page-item"><a href="#" class="page-link">7</a></li>
    <li @click="pag7" class="page-item"><a href="#" class="page-link">8</a></li>
    <li @click="pag8" class="page-item"><a href="#" class="page-link">9</a></li>
    <li @click="pag9" class="page-item"><a href="#" class="page-link">10</a></li>
    <li @click="pag10" class="page-item"><a href="#" class="page-link">11</a></li>
    <li @click="pag11" class="page-item"><a href="#" class="page-link">12</a></li>
    <li @click="pag12" class="page-item"><a href="#" class="page-link">13</a></li>
    <li @click="pag13" class="page-item"><a href="#" class="page-link">14</a></li>
    <li @click="pag14" class="page-item"><a href="#" class="page-link">15</a></li>
    <li @click="pag15" class="page-item"><a href="#" class="page-link">16</a></li>
    <li @click="pag16" class="page-item"><a href="#" class="page-link">17</a></li>

    <li  v-if="this.pokeapi.offset!==960" @click="proximapagPoke" class="page-item">
      <a href="#" class="page-link">Proximo</a>
    </li>

      </ul>
    </nav>
  </div>
  

    <div  class="container"> 
    <div class="row justify-content-center">
      <ReposTec v-for="pokemon in pokemon" :key="pokemon.id" :pokemon="pokemon"/>
    </div>
    </div>


  <div>
    <nav>
        <ul class="pagination justify-content-center">
    <li v-if="this.pokeapi.offset>0" @click="anteriorpagPoke" class="page-item">
      <a class="page-link" href="#">Anterior</a>
    </li>
    <li @click="pag0" class="page-item"><a href="#" class="page-link">1</a></li>
    <li @click="pag1" class="page-item"><a href="#" class="page-link">2</a></li>
    <li @click="pag2" class="page-item"><a href="#" class="page-link">3</a></li>
    <li @click="pag3" class="page-item"><a href="#" class="page-link">4</a></li>
    <li @click="pag4" class="page-item"><a href="#" class="page-link">5</a></li>
    <li @click="pag5" class="page-item"><a href="#" class="page-link">6</a></li>
    <li @click="pag6" class="page-item"><a href="#" class="page-link">7</a></li>
    <li @click="pag7" class="page-item"><a href="#" class="page-link">8</a></li>
    <li @click="pag8" class="page-item"><a href="#" class="page-link">9</a></li>
    <li @click="pag9" class="page-item"><a href="#" class="page-link">10</a></li>
    <li @click="pag10" class="page-item"><a href="#" class="page-link">11</a></li>
    <li @click="pag11" class="page-item"><a href="#" class="page-link">12</a></li>
    <li @click="pag12" class="page-item"><a href="#" class="page-link">13</a></li>
    <li @click="pag13" class="page-item"><a href="#" class="page-link">14</a></li>
    <li @click="pag14" class="page-item"><a href="#" class="page-link">15</a></li>
    <li @click="pag15" class="page-item"><a href="#" class="page-link">16</a></li>
    <li @click="pag16" class="page-item"><a href="#" class="page-link">17</a></li>
    <li  v-if="this.pokeapi.offset!==960" @click="proximapagPoke" class="page-item">
      <a href="#" class="page-link">Proximo</a>
    </li>
      </ul>
    </nav>
    
  </div>
  </div>

</template>
<script>

import ReposTec from'./components/ReposTec.vue';
import axios from "axios";


const API_URL = "http://localhost:3000/"
var visibilidadeTec = 0
var visibilidadeUser = 0

export default {
   mounted() {
     this.getPoke()
  },
  name: 'App',
  data(){
    return{
      pokeapi:{
        urlPoke:"https://pokeapi.co/api/v2/pokemon/" ,
        offset:0,
      },
      github:{
        urlTec:"https://api.github.com" ,
        urlUser:'https://api.github.com/users',
        client_id:'40a57736385abed0fc27',
        client_secret:'7d5ef09a9c9c8b5b22d1d17c5b4afcc5f38224d1',
        count: 1000,
        sort:'created: asc'
      },
      pokemon:[],
      user:[],
      tec:[],
      reposTec:[],
      repos:[],
      pag: 1,
      tecEscolhida:"",
      visibilidadeUser:false,
      visibilidadeTec:false,
    }
  },
  components:{

    ReposTec,
    
  },
  methods:{
    getPoke(){
      const {offset,urlPoke} = this.pokeapi
      axios.get(`${urlPoke}?offset=${offset}&limit=60`).then(({data})=> this.pokemon = data["results"])
      this.testar()},

      proximapagPoke(){
      var proximoPoke = this.pokeapi.offset + 60
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
      anteriorpagPoke(){
      var proximoPoke = this.pokeapi.offset - 60
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },


  testar(){
    console.log(this.pokemon)
  },
  pag0(){
      var proximoPoke = this.pokeapi.offset = 0
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag1(){
      var proximoPoke = this.pokeapi.offset = 60
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag2(){
      var proximoPoke = this.pokeapi.offset = 120
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag3(){
      var proximoPoke = this.pokeapi.offset = 180
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag4(){
      var proximoPoke = this.pokeapi.offset = 240
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag5(){
      var proximoPoke = this.pokeapi.offset = 300
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag6(){
      var proximoPoke = this.pokeapi.offset = 360
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag7(){
      var proximoPoke = this.pokeapi.offset = 420
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag8(){
      var proximoPoke = this.pokeapi.offset = 480
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag9(){
      var proximoPoke = this.pokeapi.offset = 540
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag10(){
      var proximoPoke = this.pokeapi.offset = 600
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag11(){
      var proximoPoke = this.pokeapi.offset = 660
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag12(){
      var proximoPoke = this.pokeapi.offset = 720
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag13(){
      var proximoPoke = this.pokeapi.offset = 780
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag14(){
      var proximoPoke = this.pokeapi.offset = 840
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag15(){
      var proximoPoke = this.pokeapi.offset = 900
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  pag16(){
      var proximoPoke = this.pokeapi.offset = 960
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke, this.pokeapi.offset)
      },
  }
  }


</script>




