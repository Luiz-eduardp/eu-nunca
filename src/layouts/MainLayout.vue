<template>
  <q-layout view="lHh lpR lFr">

    <q-header reveal elevated class=" text-white" height-hint="98" style="background-color:rgb(88 32 149)">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />

        <q-toolbar-title>
          <q-avatar>
            <img src="../assets/cerveja.png">
          </q-avatar>
          Eu Nunca!
          
        </q-toolbar-title>
         <q-select outlined v-model="model" :options="options" label="Linguagem" />
      </q-toolbar>
 <q-tabs align="left">
        <q-route-tab to="/" label="Início" />
        <q-route-tab to="/tags"  label="Modos de Jogo" />
        <q-route-tab to="/page3" label="Sugestões" />
      </q-tabs>
     
    </q-header>

    <q-drawer show-if-above v-model="leftDrawerOpen" side="left" elevated>
      <!-- drawer content -->
      <q-card dark bordered class="bg-grey-9 my-card">
      <q-card-section>
        <div class="text-h6">Eu nunca Versão 2.0</div>
        <div class="text-subtitle2">CWB GAME STUDIO<br>Última atualização da base de dados das frases: {{attDate}}</div>
      </q-card-section>

      <q-separator dark inset />

      <q-card-section>
       redes sociais: <br>
       <div class="row">


   
   <q-btn type="a" href="https://instagram.com/cwbgamestudio" label="Instagram"></q-btn>
  
   <q-btn type="a" href="https://instagram.com/cwbgamestudio" label="Facebook"></q-btn>
     
   <q-btn type="a" href="https://instagram.com/cwbgamestudio" label="Website"></q-btn>



       </div>
      </q-card-section>
    </q-card>

    
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script>
import { ref } from 'vue'

export default {
  setup () {
   
    const leftDrawerOpen = ref(false)

    return {
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  },
   created() {
 
  fetch("https://api.npoint.io/841d5e98dcf7cb9d960b/0")
    .then(response => response.json())
    .then(data => (this.attDate = data));
    
},
   data() {
      return {
        attDate:'',
         model:'',
      options: [
        'pt_BR', 'en_Us'
      ]
      }
    },
}
</script>