
<template>
  <div class="bg-danger">
    <div class="container" id="app">
        
   <div>
    <nav>
        <ul class="pagination pagination-lg justify-content-center">
    <li @click="pag0" class="page-item"><a href="#" class="page-link">Primeira Pág</a></li>
    <li v-if="this.pokeapi.offset>0" @click="anteriorpagPoke" class="page-item">
      <a class="page-link" href="#">Anterior</a>
    </li>
    <li @click="pag0"  class="page-item" v-bind:class="ativo1"><a href="#" class="page-link">1</a></li>
    <li @click="pag1" class="page-item" v-bind:class="ativo2" ><a href="#" class="page-link">2</a></li>
    <li @click="pag2" class="page-item" v-bind:class="ativo3"><a href="#" class="page-link">3</a></li>
    <li @click="pag3" class="page-item" v-bind:class="ativo4"><a href="#" class="page-link">4</a></li>
    <li @click="pag4"  class="page-item" v-bind:class="ativo5"><a href="#" class="page-link">5</a></li>
    <li @click="pag5" class="page-item" v-bind:class="ativo6"><a href="#" class="page-link">6</a></li>
    <li @click="pag6" class="page-item" v-bind:class="ativo7"><a href="#" class="page-link">7</a></li>
    <li @click="pag7" class="page-item" v-bind:class="ativo8"><a href="#" class="page-link">8</a></li>
    <li @click="pag8" class="page-item" v-bind:class="ativo9"><a href="#" class="page-link">9</a></li>
    <li @click="pag9" class="page-item" v-bind:class="ativo10"><a href="#" class="page-link">10</a></li>
    <li @click="pag10" class="page-item" v-bind:class="ativo11"><a href="#" class="page-link">11</a></li>
    <li @click="pag11" class="page-item" v-bind:class="ativo12"><a href="#" class="page-link">12</a></li>
    <li @click="pag12" class="page-item" v-bind:class="ativo13"><a href="#" class="page-link">13</a></li>
    <li @click="pag13" class="page-item" v-bind:class="ativo14"><a href="#" class="page-link">14</a></li>
    <li @click="pag14" class="page-item" v-bind:class="ativo15"><a href="#" class="page-link">15</a></li>
    <li  v-if="this.pokeapi.offset!==840" @click="proximapagPoke" class="page-item">
      <a href="#" class="page-link">Proximo</a>
    </li>
      <li @click="pag14" class="page-item"><a href="#" class="page-link">Ultima Pág</a></li>

      </ul>
    </nav>
    
  </div>
  

    <div  class="container"> 
    <div class="row justify-content-center">
      <ReposTec v-for="pokemon in pokemon" :key="pokemon.count" :pokemon="pokemon"/>
    </div>
    </div>


  <div>
    <nav>
        <ul class="pagination pagination-lg justify-content-center">
    <li @click="pag0" class="page-item"><a href="#" class="page-link">Primeira Pág</a></li>
    <li v-if="this.pokeapi.offset>0" @click="anteriorpagPoke" class="page-item">
      <a class="page-link" href="#">Anterior</a>
    </li>
    <li @click="pag0"  class="page-item" v-bind:class="ativo1"><a href="#" class="page-link">1</a></li>
    <li @click="pag1" class="page-item" v-bind:class="ativo2" ><a href="#" class="page-link">2</a></li>
    <li @click="pag2" class="page-item" v-bind:class="ativo3"><a href="#" class="page-link">3</a></li>
    <li @click="pag3" class="page-item" v-bind:class="ativo4"><a href="#" class="page-link">4</a></li>
    <li @click="pag4"  class="page-item" v-bind:class="ativo5"><a href="#" class="page-link">5</a></li>
    <li @click="pag5" class="page-item" v-bind:class="ativo6"><a href="#" class="page-link">6</a></li>
    <li @click="pag6" class="page-item" v-bind:class="ativo7"><a href="#" class="page-link">7</a></li>
    <li @click="pag7" class="page-item" v-bind:class="ativo8"><a href="#" class="page-link">8</a></li>
    <li @click="pag8" class="page-item" v-bind:class="ativo9"><a href="#" class="page-link">9</a></li>
    <li @click="pag9" class="page-item" v-bind:class="ativo10"><a href="#" class="page-link">10</a></li>
    <li @click="pag10" class="page-item" v-bind:class="ativo11"><a href="#" class="page-link">11</a></li>
    <li @click="pag11" class="page-item" v-bind:class="ativo12"><a href="#" class="page-link">12</a></li>
    <li @click="pag12" class="page-item" v-bind:class="ativo13"><a href="#" class="page-link">13</a></li>
    <li @click="pag13" class="page-item" v-bind:class="ativo14"><a href="#" class="page-link">14</a></li>
    <li @click="pag14" class="page-item" v-bind:class="ativo15"><a href="#" class="page-link">15</a></li>
    <li  v-if="this.pokeapi.offset!==840" @click="proximapagPoke" class="page-item">
      <a href="#" class="page-link">Proximo</a>
    </li>
      <li @click="pag14" class="page-item"><a href="#" class="page-link">Ultima Pág</a></li>

      </ul>
    </nav>
    
  </div>
  </div>
  </div>

</template>
<script>

import ReposTec from'./components/ReposTec.vue';
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
      pokemon:[],
      ativo1:{active: false},ativo2:{active: false},ativo3:{active: false},ativo4:{active: false},ativo5:{active: false},ativo6:{active: false},ativo7:{active: false},ativo8:{active: false},ativo9:{active: false},ativo10:{active: false},ativo11:{active: false},ativo12:{active: false},ativo13:{active: false},ativo14:{active: false},ativo15:{active: false}
      ,

    }
  },
  components:{

    ReposTec,
    
  },
  methods:{
    getPoke(){
      const {offset,urlPoke} = this.pokeapi
      axios.get(`${urlPoke}?offset=${offset}&limit=60`).then(({data})=> this.pokemon = data["results"])
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
  }
  }


</script>




