<script setup>
import { reactive } from 'vue'

const cards = reactive([
  { show: false },
  { show: false },
  { show: false },
  { show: false },
  { show: false },
  { show: false }
])

function toggle(index) {
  cards[index].show = !cards[index].show
}
</script>

<template>
  <v-card
    color="grey-lighten-4"
    height="200px"
    rounded="0"
    flat
  >
    <v-toolbar density="compact">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>JaMonzon ®</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-dots-vertical</v-icon>
      </v-btn>
    </v-toolbar>
    
    <v-container class="fill-height">
    <v-row align="center" justify="center">
      <v-col class="text-center">
        <h1>Bienvenido a JaMonzon®</h1>
        <v-divider></v-divider>
        <h3>Tienda especializada en la venta de productos alimenticios</h3>
      </v-col>
    </v-row>
  </v-container>

  </v-card>

  <v-carousel show-arrows="hover">
  <v-carousel-item
    src="../img/bacon.jpeg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="../img/jamon.jpg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="../img/queso.webp"
    cover
  ></v-carousel-item>
  
  <v-carousel-item
    src="../img/salsas.jpg"
    cover
  ></v-carousel-item>
</v-carousel>

<v-divider></v-divider>
<v-divider></v-divider>
<v-divider></v-divider>
<br>


<v-container>
    <v-row>
      <v-col
        v-for="(card, index) in cards"
        :key="index"
        cols="12"
        md="4"
      >
        <v-card class="mx-auto" max-width="344">
          <v-img
            height="200px"
            src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
            cover
          ></v-img>
          <v-card-title>
            Top western road trips
          </v-card-title>
          <v-card-subtitle>
            1,000 miles of wonder
          </v-card-subtitle>
          <v-card-actions>
            <v-btn color="orange-lighten-2" text="Explore"></v-btn>
            <v-spacer></v-spacer>
            <v-btn :icon="card.show ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="toggle(index)"></v-btn>
          </v-card-actions>
          <v-expand-transition>
            <div v-show="card.show">
              <v-divider></v-divider>
              <v-card-text>
                I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
              </v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-container>

  <br>
  <br>

</template>