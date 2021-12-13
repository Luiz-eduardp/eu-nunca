<template>

        <q-card class="my-card" style="background: rgb(88 32 149); color: white; width:80%">
      <q-card-section>
        <div class="text-h6">{{selectedFrase}}</div>
       
      </q-card-section>

      <q-separator />

      <q-card-actions vertical>
        <q-btn flat @click="randomFrase()"><b>Verdade</b></q-btn>
        <q-btn flat @click="randomFrase2()"><b>Desafio</b></q-btn>
      </q-card-actions>
      </q-card> 
</template>

<script>
export default {
  name:  'Eununca',
  setup () {
    return {}
  },
  created() {
     fetch("https://api.npoint.io/68f76dab078f7290a0e7")
    .then(response => response.json())
    .then(data => (this.perguntas = data));
     fetch("https://api.npoint.io/4273f9ac25dbd79aee59")
    .then(response => response.json())
    .then(data => (this.perguntas2 = data));
    
  },
  data() {
    return {
       perguntas: [],
        perguntas2: [],
         selectedFrase: 'Verdade ou Desafio',
    }},

    methods: {
  randomFrase() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas[idx]
  },
   randomFrase2() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas[idx]
  }
  },
}
</script>
