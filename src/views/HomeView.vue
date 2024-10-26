<script setup>
import { ref } from 'vue';

const cards = ref([
  {
    image: '../img/baconcadet.jpg',
    title: 'Bacon Cadet',
    subtitle: '$XXX',
    text: "I'm a thing. But, like most politicians, he promised more than he could deliver.",
    show: false
  },
  {
    image: '../img/baconcocido.jpg',
    title: 'Bacon cocido Sant Dalmai',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/cereales.jpg',
    title: 'Cereales',
    subtitle: '$XXX',
    text: "I'm a thing. But, like most politicians, he promised more than he could deliver.",
    show: false
  },
  {
    image: '../img/fiambrelomo.jpg',
    title: 'Fiambre de lomo adobado Sant Dalmai',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/ham.jpg',
    title: 'Jamon Sant Dalmai',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/milk.jpg',
    title: 'Leche entera en polvo',
    subtitle: '$XXX',
    text: "I'm a thing. But, like most politicians, he promised more than he could deliver.",
    show: false
  },
  {
    image: '../img/olives.jpg',
    title: 'Aceitunas',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/quesocheddar.jpg',
    title: 'Queso Cheddar',
    subtitle: '$XXX',
    text: "I'm a thing. But, like most politicians, he promised more than he could deliver.",
    show: false
  },
  {
    image: '../img/quesogouda.jpg',
    title: 'Queso Gouda',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/quesogoudarounded.jpg',
    title: 'Queso Gouda',
    subtitle: '$XXX',
    text: "I'm a thing. But, like most politicians, he promised more than he could deliver.",
    show: false
  },
  {
    image: '../img/quesohollandia.jpg',
    title: 'Queso Hollandia',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/quesomozzarella.jpg',
    title: 'Queso Mozzarella',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },
  {
    image: '../img/tomato.jpg',
    title: 'Pasta de Tomate',
    subtitle: '$XXX',
    text: "Discover the beauty of nature and enjoy the tranquility of the forests.",
    show: false
  },

]);

const cart = ref([]); // Arreglo para almacenar productos en el carrito

const toggle = (index) => {
  cards.value[index].show = !cards.value[index].show;
};

const addToCart = (product) => {
  cart.value.push(product); // Añade el producto al carrito
  console.log(`Producto añadido al carrito: ${product.title}`);
};
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
        <v-icon>mdi-cart</v-icon>
      </v-btn>

      <v-btn icon>
        <v-icon>mdi-magnify</v-icon>
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
    src="../img/bacon-4342494_1920.jpg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="../img/jamon.jpg"
    cover
  ></v-carousel-item>

  <v-carousel-item
    src="../img/cheese-4016647_1920.jpg"
    cover
  ></v-carousel-item>
  
  <v-carousel-item
    src="../img/glasses-6989171_1920.jpg"
    cover
  ></v-carousel-item>
</v-carousel>

<v-container>
    <v-row align="center" justify="center">
      <v-col class="text-center">
        <h1>Productos en Stock</h1>
      </v-col>
    </v-row>
  </v-container>

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
            :src="card.image"
            cover
          ></v-img>
          <v-card-title>
            {{ card.title }}
          </v-card-title>
          <v-card-subtitle>
            {{ card.subtitle }}
          </v-card-subtitle>
          <v-card-actions>
            <v-btn color="orange-lighten-2" text="Explore"></v-btn>
            <v-spacer></v-spacer>
            <v-btn :icon="card.show ? 'mdi-chevron-up' : 'mdi-chevron-down'" @click="toggle(index)"></v-btn>
            <v-btn icon @click="addToCart(card)">
              <v-icon>mdi-cart</v-icon>
            </v-btn>
          </v-card-actions>
          <v-expand-transition>
            <div v-show="card.show">
              <v-divider></v-divider>
              <v-card-text>
                {{ card.text }}
              </v-card-text>
            </div>
          </v-expand-transition>
        </v-card>
      </v-col>
    </v-row>
  </v-container>

    <v-footer color="grey darken-3">
      <v-row justify="center">
        <v-col class="text-center">
          <p class="white--text">&copy; 2024 JaMonzon. Todos los derechos reservados.</p>
          <p>
            <v-btn text href="/politica-privacidad" class="white--text">Política de Privacidad</v-btn>
            |
            <v-btn text href="/terminos-servicio" class="white--text">Términos de Servicio</v-btn>
          </p>
          <p class="white--text">
            Síguenos en: 
            <v-btn text href="https://facebook.com" target="_blank" class="white--text">
              <v-icon>mdi-facebook</v-icon>
            </v-btn>
            <v-btn text href="https://instagram.com" target="_blank" class="white--text">
              <v-icon>mdi-instagram</v-icon>
            </v-btn>
            <v-btn text href="https://twitter.com" target="_blank" class="white--text">
              <v-icon>mdi-twitter</v-icon>
            </v-btn>
            <v-btn text href="https://twitter.com" target="_blank" class="white--text">
              <v-icon>mdi-whatsapp</v-icon>
            </v-btn>
          </p>
        </v-col>
      </v-row>
    </v-footer>

</template>

<style scoped>

</style>