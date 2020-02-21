
<template>
  <div id="app">
        

    <div class="">
    <div  class="row mt-6"> 
    <div class="row col">
      <ReposTec v-for="pokemon in pokemon" :key="pokemon" :pokemon="pokemon"/>
    </div>
    </div>



    </div>
    <div>
      <button  class="btn btn-info" @click="proximaPag">testar codigo</button>
      <button  class="btn btn-info" @click="testar">testar pokemon</button>
      <button  class="btn btn-info" @click="proximapagPoke">testar pag</button>

    </div>
  </div>
</template>
<script>

import ReposTec from'./components/ReposTec.vue';



import axios from "axios";
import API from "./lib/API";

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

    ReposTec
    
  },
  methods:{
    getPoke(){
      const {offset,urlPoke} = this.pokeapi
      axios.get(`${urlPoke}?offset=${offset}&limit=30`).then(({data})=> this.pokemon = data["results"])
      },

      proximapagPoke(){
      var proximoPoke = this.pokeapi.offset + 30
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      console.log(proximoPoke)
      console.log(this.pokeapi.offset)
      },


  testar(){
    console.log(this.pokemon)
  },


    getUser(e){
      const {pag,urlTec,client_id,client_secret} = this.github

      axios.get(`${urlUser}/${user}?client_id=${client_id}&client_secret=${client_secret}`) 
      .then(({data})=>this.user = (this.user = data))

      axios.get(`${urlUser}/${user}/repos?per_page=${count}&sort=${sort}&client_id=${client_id}&client_secret=${client_secret}`)
      .then(({data})=> this.repos = data)
    }
    
    
    ,
    proximaPag(e){
      const proximaPag = this.pag++
      const tec = e.target.value;
      const {pag,urlTec,client_id,client_secret} = this.github
      console.log(this.reposTec)

      axios.get(`${urlTec}/search/repositories?q=language:${this.tecEscolhida}&sort=stars&page=${proximaPag}&client_id=${client_id}&client_secret=${client_secret}`) 
      .then(({data})=>this.reposTec = data.items)
      },
    getTec(e){
      const tec = e.target.value;
      const {pag,urlTec,client_id,client_secret} = this.github
      this.tecEscolhida = tec

      axios.get(`${urlTec}/search/repositories?q=language:${tec}&sort=stars&page=1&client_id=${client_id}&client_secret=${client_secret}`) 
      .then(({data})=>this.tec = (this.tec = data))
      
      axios.get(`${urlTec}/search/repositories?q=language:${tec}&sort=stars&page=${pag}&client_id=${client_id}&client_secret=${client_secret}`) 
      .then(({data})=>this.reposTec = data.items)

    }
    
  }
  }


</script>




