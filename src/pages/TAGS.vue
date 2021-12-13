<template>
  <div class="q-pa-md">
 

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
  </div>
  <q-page-container style="padding-top: 50px !important">
    <component v-bind:is="gamemode"></component>
  </q-page-container>
</template>

<script>
import { defineComponent } from "vue";
import { ref } from "vue";
import Eununca from "../components/Eununca.vue";
import VerdadeorDesafio from "../components/VerdadeorDesafio.vue";
import MaisProvavel from "../components/MaisProvavel.vue";
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
      ],
    };
  },
  name: "Tags",
  components: {
    Eununca,
    VerdadeorDesafio,
    MaisProvavel,
  },
  data() {
    return {
      gamemode: "Eununca",
    };
  },
});
</script>
