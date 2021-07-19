<template>
  <v-app>
    <v-container>
      <v-row class="justify-center">
        <v-col cols="3" sm="3" md="3" lg="3">
          <v-img src="@/assets/ramo_de_globos.png" alt="Ramo de blobos"></v-img>
        </v-col>
        <v-col cols="6" sm="6" md="6" lg="6">
          <h1 align="center" class="mt-6 mb-6">Felíz Cumpleaños Dany</h1>
        </v-col>
        <v-col cols="3" sm="3" md="3" lg="3">
          <v-img src="@/assets/ramo_de_globos.png" alt="Ramo de blobos"></v-img>
        </v-col>
      </v-row>
      <v-row class="justify-center">
        <p>Abre tu regalo</p>
      </v-row>
      <v-row class="justify-center">
        <p>(Puchale a la cajita)</p>
      </v-row>
      <v-row class="justify-center" id="gb">
        <giftbox />
      </v-row>
      
      <v-carousel class="mb-6" height="700" cycle interval="5000" >
        <v-carousel-item 
          v-for="(item,i) in items" 
          :key="i" 
          :src="item.src" 
        >
        </v-carousel-item>
      </v-carousel>
      <div class="text-center">
        <h4>Unas palabras de mí para tururu</h4>
      </div>
      <br>
      <!-- Video -->
      <div class="d-flex align-center mx-auto" :style="{width: '960px'}">
        <player />
      </div>
    </v-container>
    <v-footer dark padless fixed>
      <v-card class="flex" flat tile>
        <v-card-text class="py-2 white--text text-center">
         <strong>Have a nice day!</strong>
        </v-card-text>
      </v-card>
  </v-footer>
  </v-app>
</template>

<script>
import player from "./Player/player.vue"
import giftbox from "./GiftBox.vue"

export default {
  name: 'home',
  components: {
    player,
    giftbox
  },
  data: () => ({
    colors: [
      'indigo',
      'warning',
      'pink darken-2',
      'red lighten-1',
      'deep-purple accent-4',
    ],
    slides: [
      'First',
      'Second',
      'Third',
      'Fourth',
      'Fifth',
    ],
    items: [
      {
        src: require('@/assets/uno.jpg')
      },
      {
        src: require('@/assets/dos.jpg')
      },
      {
        src: require('@/assets/tres.jpg')
      },
      {
        src: require('@/assets/cuatro.jpg')
      },
      {
        src: require('@/assets/cinco.jpg')
      }
    ]
  }),
  
  methods: {

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url('https://fonts.googleapis.com/css2?family=Zen+Tokyo+Zoo&display=swap');
  @import url('https://fonts.googleapis.com/css2?family=Otomanopee+One&display=swap');

  h1 {
    color: aquamarine;
    font-family: 'Indian Type Foundry', cursive;
  }

  h4 {
    color: aquamarine;
  }

  p {
    color: azure;
    font-size: 1em;
    font-family: 'Otomanopee One', sans-serif;;
  }
  #gb {
    margin-bottom: 420px;
  }
</style>
