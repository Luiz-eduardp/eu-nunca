<template>

        <q-card class="my-card" style="background: rgb(88 32 149); color: white; width:80%">
             <q-input filled v-model="jogadores" label="Jogadores" />
              <q-btn flat @click=" randomUser()"><b>Começar</b></q-btn>
             <q-card-section> Vez de {{jogador}}</q-card-section>
          <q-card-section v-show="timerEnabled">
           Restam  {{ timerCount }} segundos
          </q-card-section>
      <q-card-section v-show="timerEnabled">
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
      jogadores:['luiz', 'eduardo'],
      jogador:'',
      timerCount: 10,
      timerEnabled: false,
       perguntas: [],
        perguntas2: [],
         selectedFrase: 'Verdade ou Desafio',
    }},
  watch: {

            timerEnabled(value) {
                if (value) {
                    setTimeout(() => {
                        this.timerCount--;
                    }, 1000);
                }
            },

            timerCount: {
                handler(value) {

                    if (value > 0 && this.timerEnabled) {
                        setTimeout(() => {
                            this.timerCount--;
                        }, 1000);
                    }

                },
                immediate: true 
            }

        },
    methods: {
  randomFrase() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas[idx]
    this.timerEnabled = true 
    setTimeout(() => {
          this.timerEnabled = false,
           this.timerCount = 10 ,
            randomUser()
    }, 10000);
  },
   randomFrase2() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
    this.selectedFrase = this.perguntas2[idx]
    this.timerEnabled = true 
    setTimeout(() => {
          this.timerEnabled = false,
           this.timerCount = 10 ,
           randomUser()
    }, 10000);
  },
    randomUser(){

       const ixcdx = Math.floor(Math.random() * this.jogadores.length);
    this.jogador = this.jogadores[ixcdx]
    }

  },
}
</script>
