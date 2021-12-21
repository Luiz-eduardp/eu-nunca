<template>
  <div class="q-pa-md row">
 

    <q-select
    color="purple" outlined label-color="purple"
      label="Modos de Jogo"
      transition-show="jump-up "
      transition-hide="jump-up"
      filled
      v-model="gamemode"
      :options="options"
      style="width: 250px"
        emit-value
         map-options
    />
     <q-btn flat @click=" regrasRow = !regrasRow, regraVdd = false, regraprov = false, regraEn = false" style="background-color:#582095"><b>Regras</b></q-btn>
      
  </div>

<div  v-show="regrasRow" class="row"> 
  <q-btn flat @click=" regraEn = !regraEn, regraVdd = false, regraprov = false" style="background-color:#582095"><b>Eu nunca</b></q-btn> 
  
  <q-btn flat @click=" regraVdd = !regraVdd, regraEn = false, regraprov = false" style="background-color:#582095"><b>Verdade ou Desafio</b></q-btn>
        <q-btn flat @click=" regraprov = !regraprov, regraEn = false, regraVdd = false" style="background-color:#582095"><b>Quem é mais provável?</b></q-btn>
  
  </div>
  <q-card-section v-show="regraEn">
Clique em próximo para novas frases, todos que já fizeram a ação da frase mostrada devem tomar um shot.
  </q-card-section>
  <q-card-section v-show="regraVdd">

Escolham uma pessoa  quem vai começar.<br>
O sortudo vai escolher uma pessoa para perguntar <br>
Cada um só pode usar 2 verdades seguidas.<br>
Quem não cumprir o desafio deve 2 reais para cada participante<br>
  </q-card-section>
  <q-card-section v-show="regraprov">
Clique em próximo para novas frases, veja quem é mais provável de fazer a ação.
  </q-card-section>
  <q-page-container style="padding-top: 50px !important;">
    <component v-bind:is="gamemode"></component>
  </q-page-container>
</template>

<script>
import { defineComponent } from "vue";
import { ref } from "vue";
import Eununca from "../components/Eununca.vue";
import VerdadeorDesafio from "../components/VerdadeorDesafio.vue";
import MaisProvavel from "../components/MaisProvavel.vue";
import Oqvcprefere from "../components/Oqvcprefere.vue";
import funfacts from "../components/funfacts.vue";
export default defineComponent({
  setup() {
    return {
      model: ref(null),
      options: [
        {
          label: "Eu Nunca",
          value: "Eununca",
        },
         {
          label: "Verdade ou Desafio",
          value: "VerdadeorDesafio",
        },
         {
          label: "Quem é mais provável?",
          value: "MaisProvavel",
        },
        {
          label: "O que você prefere?",
          value: "Oqvcprefere"
        },
         {
          label: "Fatos engraçados",
          value: "funfacts"
        }
      ],
    };
  },
  name: "Tags",
  components: {
    Eununca,
    VerdadeorDesafio,
    MaisProvavel,
    Oqvcprefere,
    funfacts
  },
  data() {
    return {
      regraEn: false,
      regraprov: false,
      regraVdd: false,
      regrasRow: false,
      regras: false,
      gamemode: "Eununca",
    };
  },
});
</script>
