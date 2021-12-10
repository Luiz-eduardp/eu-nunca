<template>
  <q-page class="flex flex-center">
    <q-card class="my-card" style="background: rgb(88 32 149); color: white; width:80%">
      <q-card-section>
        <div class="text-h6">{{selectedFrase}}</div>
       
      </q-card-section>

      <q-separator />

      <q-card-actions vertical>
        <q-btn flat @click="randomFrase()"><b>Próximo</b></q-btn>
        
      </q-card-actions>
    </q-card>

  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  
  name: "PageIndex",
  data() {
    return {
      perguntas: [],
      selectedFrase: 'Clique para gerar uma frase',
    }
  },
  created() {
 
  fetch("https://api.npoint.io/972d58dae1664aafb96a/")
    .then(response => response.json())
    .then(data => (this.perguntas = data));
    
},
methods: {
  randomFrase() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas[idx]
  },
},
});
</script>
