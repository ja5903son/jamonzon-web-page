<script setup>

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
        <h3>Tienda especializada en la venta de productos alimenticios</h3>
      </v-col>
    </v-row>
  </v-container>

  </v-card>

  <v-carousel show-arrows="hover">
  <v-carousel-item
    src="https://cdn.vuetifyjs.com/images/cards/docks.jpg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="https://cdn.vuetifyjs.com/images/cards/hotel.jpg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
    cover
  ></v-carousel-item>
  
  <v-carousel-item
    src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
    cover
  ></v-carousel-item>
</v-carousel>
</template>