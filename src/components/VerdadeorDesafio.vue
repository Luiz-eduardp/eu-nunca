<template>
  <q-card>
   
    <q-btn flat @click="verPlayers()"> Jogadores </q-btn>
    <p
      style="padding-left: 20px"
      v-show="mostrarplayers"
      v-for="(jogador, i) in jogadores"
      :key="i"
    >
      <span>{{ jogadores[i] }}</span>
    </p>
    <q-input
      v-show="mostrarplayers"
      standout="bg-purple text-white"
      v-model="jogadorname"
      label="Adicionar novos jogadores"
    />
    <q-btn
      flat
      v-show="mostrarplayers"
      @click="addjogador()"
      @change="this.podeadd = true"
      ><b>+1 jogador</b></q-btn
    >
  </q-card>
  <q-card
    class="my-card"
    style="background: rgb(88 32 149); color: white; margin-top: 30px"
  >
    <q-card-section v-show="timerEnabled">
      Restam {{ timerCount }} segundos
    </q-card-section>
    <q-card-section v-show="timerEnabled" style="text-align: center">
      <div class="text-h6">{{ selectedFrase }}</div>
    </q-card-section>

    <q-separator />

  </q-card>
  <q-banner
    dense
    inline-actions
    class="text-white bg-purple"
    style="margin-top: 30px"
  >
    Vez de {{ vezde }} perguntar para {{ perguntapara }}
    <template v-slot:action>
      <q-btn v-show="!timerEnabled" flat color="white" label="Nova Rodada" @click="randomPlayer()" />
      
    <q-card-actions vertical v-show="!timerEnabled">
      <q-btn flat @click="randomFrase()"><b>Verdade</b></q-btn>
      <q-btn flat @click="randomFrase2()"><b>Desafio</b></q-btn>
    </q-card-actions>
    </template>
  </q-banner>
</template>

<script>
import { useQuasar } from "quasar";

export default {
  name: "Eununca",
  setup() {
    const $q = useQuasar();

    return {
      showNotif() {
        $q.notify({
          message: "Jim pinged you.",
          caption: "5 minutes ago",
          color: "secondary",
        });
      },
    };
  },
  created() {
    fetch("https://api.npoint.io/68f76dab078f7290a0e7")
      .then((response) => response.json())
      .then((data) => (this.perguntas = data));
    fetch("https://api.npoint.io/4273f9ac25dbd79aee59")
      .then((response) => response.json())
      .then((data) => (this.perguntas2 = data));
  },
  data() {
    return {
      jogadorname: "",
      jogadores: [],
      podeadd: true,
      mostrarplayers: false,
      vezde: "Alguém",
      perguntapara: "Alguém",
      timerCount: 10,
      timerEnabled: false,
      perguntas: [],
      perguntas2: [],
      selectedFrase: "Verdade ou Desafio",
    };
  },
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
      immediate: true,
    },
  },
  methods: {
    verPlayers() {
      this.mostrarplayers = !this.mostrarplayers;
    },

    addjogador: function () {
      if (this.jogadorname != "") {
        this.jogadores.push(this.jogadorname);
        this.jogadorname = "";
      } else this.jogadorname = "Escreva um nome aqui antes";
    },

    randomFrase() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
      this.selectedFrase = this.perguntas[idx];
      this.timerEnabled = true;
      setTimeout(() => {
        (this.timerEnabled = false), (this.timerCount = 10);
      }, 10000);
    },
    randomFrase2() {
      const idx = Math.floor(Math.random() * this.perguntas.length);
      (this.selectedFrase = this.perguntas2[idx]), (this.timerEnabled = true);
      setTimeout(() => {
        (this.timerEnabled = false), (this.timerCount = 10);
      }, 10000);
    },
    randomPlayer() {
      const idx = Math.floor(Math.random() * this.jogadores.length);
       const idx2 = Math.floor(Math.random() * this.jogadores.length);
     
        if (idx != idx2) {
                this.vezde = this.jogadores[idx];
      this.perguntapara =
        this.jogadores[idx2];
        } else {
      randomPlayer2();
        }
    },
    randomPlayer2() {
      const ixdx = Math.floor(Math.random() * this.jogadores.length);

      this.perguntapara = this.jogadores[ixdx];
    },
  },
};
</script>
