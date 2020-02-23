
<template>

  <div class="bg-danger ">
    <div>
      <nav class="navbar navbar-light bg-light">
      <h1 class="navbar"  href="#">
      <img src="https://cdn4.iconfinder.com/data/icons/gaming-27/300/gaming-fun-entertainment-freetime-pokemon-512.png" width="60" height="60" class="d-inline-block align-top">
      Pokedex
      </h1>
      </nav>
    </div>
    <div class="container" id="app">
        
   <div class="container-fluid">
    <nav>
        <ul class="pagination pagination-lg justify-content-center">
    <li v-if="this.pokeapi.offset>0" @click="pag0" class="page-item"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">&laquo;&laquo;&laquo;Primeiro</a></li>
    <li v-if="this.pokeapi.offset>0" @click="anteriorpagPoke" class="page-item"><a class="page-link border border-dark rounded-lg font-weight-bold " href="#">&laquo;Anterior</a></li>
    <li @click="pag0"  class="page-item" v-bind:class="ativo1"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold ">1</a></li>
    <li @click="pag1" class="page-item" v-bind:class="ativo2" ><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">2</a></li>
    <li @click="pag2" class="page-item" v-bind:class="ativo3"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">3</a></li>
    <li @click="pag3" class="page-item" v-bind:class="ativo4"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">4</a></li>
    <li @click="pag4"  class="page-item" v-bind:class="ativo5"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">5</a></li>
    <li @click="pag5" class="page-item" v-bind:class="ativo6"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">6</a></li>
    <li @click="pag6" class="page-item" v-bind:class="ativo7"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">7</a></li>
    <li @click="pag7" class="page-item" v-bind:class="ativo8"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">8</a></li>
    <li @click="pag8" class="page-item" v-bind:class="ativo9"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">9</a></li>
    <li @click="pag9" class="page-item" v-bind:class="ativo10"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">10</a></li>
    <li @click="pag10" class="page-item" v-bind:class="ativo11"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">11</a></li>
    <li @click="pag11" class="page-item" v-bind:class="ativo12"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">12</a></li>
    <li @click="pag12" class="page-item" v-bind:class="ativo13"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">13</a></li>
    <li @click="pag13" class="page-item" v-bind:class="ativo14"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">14</a></li>
    <li @click="pag14" class="page-item" v-bind:class="ativo15"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">15</a></li>
    <li  v-if="this.pokeapi.offset!==840" @click="proximapagPoke" class="page-item"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">Próximo&raquo;</a></li>
    <li v-if="this.pokeapi.offset!==840" @click="pag14" class="page-item"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">Ultimo&raquo;&raquo;&raquo;</a></li>
        </ul>
    </nav>
  </div>
  

    <div  class="container"> 
    <div class="row justify-content-center">
      <PokemonVue v-for="pokemon in pokemons" :key="pokemon.name" :pokemon="pokemon"/>
    </div>
    </div>


  <div class="container-fluid">
    <nav>
        <ul class="pagination pagination-lg justify-content-center">
    <li v-if="this.pokeapi.offset>0" @click="pag0" class="page-item"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">&laquo;&laquo;&laquo;Primeiro</a></li>
    <li v-if="this.pokeapi.offset>0" @click="anteriorpagPoke" class="page-item"><a class="page-link border border-dark rounded-lg font-weight-bold " href="#">&laquo;Anteiror </a></li>
    <li @click="pag0"  class="page-item" v-bind:class="ativo1"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">1</a></li>
    <li @click="pag1" class="page-item" v-bind:class="ativo2" ><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">2</a></li>
    <li @click="pag2" class="page-item" v-bind:class="ativo3"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">3</a></li>
    <li @click="pag3" class="page-item" v-bind:class="ativo4"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">4</a></li>
    <li @click="pag4"  class="page-item" v-bind:class="ativo5"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">5</a></li>
    <li @click="pag5" class="page-item" v-bind:class="ativo6"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">6</a></li>
    <li @click="pag6" class="page-item" v-bind:class="ativo7"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">7</a></li>
    <li @click="pag7" class="page-item" v-bind:class="ativo8"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">8</a></li>
    <li @click="pag8" class="page-item" v-bind:class="ativo9"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">9</a></li>
    <li @click="pag9" class="page-item" v-bind:class="ativo10"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">10</a></li>
    <li @click="pag10" class="page-item" v-bind:class="ativo11"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">11</a></li>
    <li @click="pag11" class="page-item" v-bind:class="ativo12"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">12</a></li>
    <li @click="pag12" class="page-item" v-bind:class="ativo13"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">13</a></li>
    <li @click="pag13" class="page-item" v-bind:class="ativo14"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">14</a></li>
    <li @click="pag14" class="page-item" v-bind:class="ativo15"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">15</a></li>
    <li  v-if="this.pokeapi.offset!==840" @click="proximapagPoke" class="page-item"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">Próximo&raquo;</a></li>
    <li v-if="this.pokeapi.offset!==840" @click="pag14" class="page-item"><a href="#" class="page-link border border-dark rounded-lg font-weight-bold">Ultimo&raquo;&raquo;&raquo;</a></li>
        </ul>
    </nav>
  </div>
  </div>
  </div>

</template>
<script>

import PokemonVue from'./components/PokemonVue.vue';
import axios from "axios";


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
      pokemons:[],
      ativo1:{active: false},ativo2:{active: false},ativo3:{active: false},ativo4:{active: false},ativo5:{active: false},ativo6:{active: false},ativo7:{active: false},ativo8:{active: false},ativo9:{active: false},ativo10:{active: false},ativo11:{active: false},ativo12:{active: false},ativo13:{active: false},ativo14:{active: false},ativo15:{active: false}
      ,

    }
  },
  components:{

    PokemonVue,
    
  },
  methods:{
    getPoke(){
      const {offset,urlPoke} = this.pokeapi
      axios.get(`${urlPoke}?offset=${offset}&limit=60`).then(({data})=> this.pokemons = data["results"])
      if(this.pokeapi.offset == 0) {
        this.ativo1.active = true;this.ativo2.active = false; this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false; this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false; this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 60) {
        this.ativo1.active = false;this.ativo2.active = true;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false; this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 120) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = true;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false; this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 180) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = true;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 240) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = true;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 300) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = true;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 360) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = true;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 420) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = true;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 480) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = true;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 540) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = true;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 600) {
        this.ativo1.active = false;this.ativo2.active = false; this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = true;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 660) {
            this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = true; this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 720) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = true;this.ativo14.active = false;this.ativo15.active = false;
      }if (this.pokeapi.offset == 780) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = true;this.ativo15.active = false;
      }if (this.pokeapi.offset == 840) {
        this.ativo1.active = false;this.ativo2.active = false;this.ativo3.active = false;this.ativo4.active = false;this.ativo5.active = false;this.ativo6.active = false;this.ativo7.active = false;this.ativo8.active = false;this.ativo9.active = false;this.ativo10.active = false;this.ativo11.active = false;this.ativo12.active = false;this.ativo13.active = false;this.ativo14.active = false;this.ativo15.active = true;
      }this.testar()
      },

  proximapagPoke(){
      var proximoPoke = this.pokeapi.offset + 60
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  anteriorpagPoke(){
      var proximoPoke = this.pokeapi.offset - 60
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  testar(){
    console.log(this.pokemon)
  },
  pag0(){
      var proximoPoke = this.pokeapi.offset = 0
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag1(){
      var proximoPoke = this.pokeapi.offset = 60
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag2(){
      var proximoPoke = this.pokeapi.offset = 120
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag3(){
      var proximoPoke = this.pokeapi.offset = 180
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag4(){
      var proximoPoke = this.pokeapi.offset = 240
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag5(){
      var proximoPoke = this.pokeapi.offset = 300
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag6(){
      var proximoPoke = this.pokeapi.offset = 360
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag7(){
      var proximoPoke = this.pokeapi.offset = 420
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag8(){
      var proximoPoke = this.pokeapi.offset = 480
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag9(){
      var proximoPoke = this.pokeapi.offset = 540
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag10(){
      var proximoPoke = this.pokeapi.offset = 600
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag11(){
      var proximoPoke = this.pokeapi.offset = 660
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag12(){
      var proximoPoke = this.pokeapi.offset = 720
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag13(){
      var proximoPoke = this.pokeapi.offset = 780
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  pag14(){
      var proximoPoke = this.pokeapi.offset = 840
      this.pokeapi.offset = proximoPoke
      this.getPoke()
      },
  }
  }


</script>




