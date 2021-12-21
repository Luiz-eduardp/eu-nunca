<template>
  <div class="q-pa-md">

    <q-banner dense inline-actions class="text-white bg-purple" style="margin-bottom:50px;">
      Novo modo de jogo adicionado, experimente: <b> Fatos Engraçados</b>
      
    </q-banner>
 <q-carousel
        v-model="slide"
        transition-prev="jump-right"
        transition-next="jump-left"
        swipeable
        animated
        control-color="white"
        prev-icon="arrow_left"
        next-icon="arrow_right"
        navigation-icon="radio_button_unchecked"
        navigation
        padding
        arrows
        height="300px"
        class="bg-purple text-white shadow-1 rounded-borders"
      >
        <q-carousel-slide name="style" class="column no-wrap flex-center">
          <q-icon name="trending_up" size="56px" />
          <div class="q-mt-md text-center">
            {{ slide1 }}
          </div>
        </q-carousel-slide>
        <q-carousel-slide name="tv" class="column no-wrap flex-center">
          <q-icon name="published_with_changes" size="56px" />
          <div class="q-mt-md text-center">
            {{ slide2 }}
          </div>
        </q-carousel-slide>
        
      </q-carousel>
  </div>
</template>
<script>
import { ref } from 'vue'

export default {
  setup () {
    return {
      slide: ref('style'),
      
      slide1: 'Mantenha todas suas reuniões com amigos animadas!',
       slide2: 'Todo o banco de dados é atualizado periodicamente!'
    }
  }
}
</script>