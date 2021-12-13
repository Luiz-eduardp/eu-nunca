<template>
<div class="q-pa-md">

    <div class="row">
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
export default defineComponent({
  
  name: "Tags",
  components: {
    Eununca,VerdadeorDesafio
  },
  data() {
    return {
      gamemode: 'Eununca',
    
    }
  },



});
</script>
