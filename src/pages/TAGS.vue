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
  <q-card class="my-card" style="background: rgb(88 32 149); color: white; width:80%">
      <q-card-section>
        <div class="text-h6">{{selectedFrase2}}</div>
       
      </q-card-section>

      <q-separator />

      <q-card-actions vertical>
        <q-btn flat @click="randomFrase2()"><b>Próximo</b></q-btn>
        
      </q-card-actions>
      </q-card>
        <q-card class="my-card" style="background: rgb(88 32 149); color: white; width:80%">
      <q-card-section>
        <div class="text-h6">{{selectedFrase3}}</div>
       
      </q-card-section>

      <q-separator />

      <q-card-actions vertical>
        <q-btn flat @click="randomFrase3()"><b>Verdade</b></q-btn>
        <q-btn flat @click="randomFrase4()"><b>Desafio</b></q-btn>
      </q-card-actions>
      </q-card>
  </q-page>
</template>

<script>
import { defineComponent } from "vue";

export default defineComponent({
  
  name: "Tags",
  data() {
    return {
      eununca:false,
      maisprovavelAmigas:false,

      maisprovavel:'"https://api.npoint.io/70e9a02571f303033fc1"',
      perguntas: [],
      perguntas2: [],
      perguntas3: [],
           perguntas4: [],
      selectedFrase: 'Eu nunca',
      selectedFrase2:'Quem é mais provavel (Amiga)',
       selectedFrase3:'Verdade ou Desafio?',
    }
  },
  created() {
   this.eununca = false
      this.maisprovavelAmigas = false
       this.selectedFrase = 'Eu nunca'
       this.selectedFrase2= 'Quem é mais provavel (Amiga)'
  fetch("https://api.npoint.io/972d58dae1664aafb96a/")
    .then(response => response.json())
    .then(data => (this.perguntas = data));
     fetch("https://api.npoint.io/70e9a02571f303033fc1")
    .then(response => response.json())
    .then(data => (this.perguntas2 = data));
      fetch("https://api.npoint.io/68f76dab078f7290a0e7")
    .then(response => response.json())
    .then(data => (this.perguntas3 = data));
     fetch("https://api.npoint.io/4273f9ac25dbd79aee59")
    .then(response => response.json())
    .then(data => (this.perguntas4 = data));
    
},
methods: {
  randomFrase() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas[idx]
  },
   randomFrase2() {
      const idx = Math.floor(Math.random() * this.perguntas2.length);
    this.selectedFrase2 = this.perguntas2[idx]
  },
   randomFrase3() {
      const idx = Math.floor(Math.random() * this.perguntas3.length);
    this.selectedFrase3 = this.perguntas3[idx]
  },
    randomFrase4() {
      const idx = Math.floor(Math.random() * this.perguntas4.length);
    this.selectedFrase3 = this.perguntas4[idx]
  },
  voltar(){
     this.eununca = false
      this.maisprovavelAmigas = false
       this.selectedFrase = 'Eu nunca'
       this.selectedFrase2= 'Quem é mais provavel (Amiga)'
  }
 
},
});
</script>
