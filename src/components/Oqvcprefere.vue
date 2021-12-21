<template>
  <q-card class="my-card" style="background: rgb(88 32 149); color: white;">

      <q-card-section style="text-align:center">
        <div class="text-h6">{{selectedFrase}}</div>
      
      </q-card-section>

      <q-separator />

      <q-card-actions vertical>
        <q-btn flat @click="randomFrase()"><b>Próximo</b></q-btn>
        
      </q-card-actions>
    </q-card>
</template>

<script>
export default {
  name:  'Oqvcprefere',
  setup () {
    return {}
  },
  created() {
    fetch("https://api.npoint.io/c80a1e6463ce6e1ec1fc")
    .then(response => response.json())
    .then(data => (this.perguntas = data));
  },
  data() {
    return {
       perguntas: [],
         selectedFrase: 'O que você prefere?',
    }},

    methods: {
  randomFrase() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas[idx]
  }
  },
}
</script>
