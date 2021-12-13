<template>
<div class="q-pa-md">

    <div class="row ro">
      <div class="col"><q-btn style="background: rgb(88 32 149); color: white; width:80%" @click="gamemode = 'Eununca'">Eu nunca</q-btn></div>
      <div class="col"><q-btn style="background: rgb(88 32 149); color: white; width:80%" @click="gamemode = 'VerdadeorDesafio'">Verdade ou Desafio</q-btn></div>
      <div class="col"><q-btn style="background: rgb(88 32 149); color: white; width:80%" @click="gamemode = 'MaisProvavel'">Quem é mais provável</q-btn></div>
  
    </div>

   

  </div>
  <q-page class="flex flex-center">

<component v-bind:is="gamemode"></component>

  </q-page>
</template>

<script>
import { defineComponent } from "vue";
import Eununca from '../components/Eununca.vue'
import VerdadeorDesafio from '../components/VerdadeorDesafio.vue'
import MaisProvavel from '../components/MaisProvavel.vue'
export default defineComponent({
  
  name: "Tags",
  components: {
    Eununca,VerdadeorDesafio,MaisProvavel
  },
  data() {
    return {
      gamemode: 'Eununca',
    
    }
  },



});
</script>

<style>
 
@media only screen and (max-width:70em) { 
	.ro{
    flex-direction: column !important;
    padding: 0 80px;
    width: 100% !important;
  }
}

</style>