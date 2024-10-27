<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue';
import { useRouter } from 'vue-router';

const items = [
  { src: '../img/bacon-4342494_1920.jpg' },
  { src: '../img/jamon.jpg' },
  { src: '../img/cheese-4016647_1920.jpg' },
  { src: '../img/glasses-6989171_1920.jpg' },
];

const currentIndex = ref(0);
let intervalId = null;

const start = () => {
  intervalId = setInterval(() => {
    currentIndex.value = (currentIndex.value + 1) % items.length;
  }, 3000);
};

const pause = () => {
  clearInterval(intervalId);
};

onMounted(() => {
  start();
});

onBeforeUnmount(() => {
  clearInterval(intervalId);
});


const cards = ref([
  {
    image: '../img/baconcadet.jpg',
    title: 'Bacon Cadet',
    subtitle: '$7000',
    text: "Caja de bacon de 5kg",
    show: false
  },
  {
    image: '../img/baconcocido.jpg',
    title: 'Bacon cocido Sant Dalmai',
    subtitle: '$7000',
    text: "Bacon cocido de 4kg",
    show: false
  },
  {
    image: '../img/cereales.jpg',
    title: 'Cereales',
    subtitle: '$800 c/u',
    text: "Cereales de 1kg c/u",
    show: false
  },
  {
    image: '../img/fiambrelomo.jpg',
    title: 'Fiambre de lomo adobado Sant Dalmai',
    subtitle: '$5000',
    text: "Fiambre de lomo adobado 2.57kg",
    show: false
  },
  {
    image: '../img/ham.jpg',
    title: 'Jamon Sant Dalmai',
    subtitle: '$12000',
    text: "Peso: 16lb",
    show: false
  },
  {
    image: '../img/milk.jpg',
    title: 'Leche entera en polvo',
    subtitle: '$2300',
    text: "Bolsa de leche en polvo de 1kg",
    show: false
  },
  {
    image: '../img/olives.jpg',
    title: 'Aceitunas',
    subtitle: '$4000',
    text: "Aceitunas lata de 4kg",
    show: false
  },
  {
    image: '../img/quesocheddar.jpg',
    title: 'Queso Cheddar',
    subtitle: '$6000',
    text: "Queso de 3kg",
    show: false
  },
  {
    image: '../img/quesogouda.jpg',
    title: 'Queso Gouda',
    subtitle: '$8000',
    text: "Queso de 3kg",
    show: false
  },
  {
    image: '../img/quesogoudarounded.jpg',
    title: 'Queso Gouda',
    subtitle: '$8000',
    text: "Queso de 4kg",
    show: false
  },
  {
    image: '../img/quesohollandia.jpg',
    title: 'Queso Hollandia',
    subtitle: '$7500',
    text: "Queso de 3.5kg",
    show: false
  },
  {
    image: '../img/quesomozzarella.jpg',
    title: 'Queso Mozzarella',
    subtitle: '$5500',
    text: "Queso de 3kg",
    show: false
  },
  {
    image: '../img/tomato.jpg',
    title: 'Pasta de Tomate',
    subtitle: '$3000',
    text: "Lata de Pasta de Tomate de 3kg",
    show: false
  },

]);

const toggle = (index) => {
  cards.value[index].show = !cards.value[index].show;
};

const cart = ref([]);
const router = useRouter();

const addToCart = (product) => {
  cart.value.push(product);
  console.log(`Producto añadido al carrito: ${product.title}`);
};
const goToCart = () => {
  router.push({ path: '/cart', query: { cart: JSON.stringify(cart.value) } });
};
</script>

<template>
<v-main id="main-content">
  <v-card
    color="#e5e5e5"
    height="200px"
    rounded="0"
    flat
  >
    <v-toolbar density="compact">
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>JaMonzon ®</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-btn icon @click="goToCart">
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

  <v-carousel v-model="currentIndex" show-arrows="hover" @mouseenter="pause" @mouseleave="start">
    <v-carousel-item
      v-for="(item, index) in items"
      :key="index"
      :src="item.src"
      cover
    ></v-carousel-item>
  </v-carousel>

<v-container>
    <v-row align ="center" justify="center">
      <v-col class="text-center">
        <h1 class="stock">Productos en Stock</h1>
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
            <v-btn color="gray" text="Datos del Producto"></v-btn>
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

    <footer >
      <v-row justify="center">
        <v-col class="text-center">
          <p class="white--text">&copy; 2024 JaMonzon. Todos los derechos reservados.</p>
          
          <p class="white--text">
            Contactenos en: 
            
            <v-btn text rounded href="https://wa.me/qr/MVONVZX53A3FJ1" target="_blank" class="white--text" id="whatsapp">
              <v-icon>mdi-whatsapp</v-icon>
            </v-btn>
            <v-btn text rounded href="https://t.me/JonathanMH03" target="_blank" class="white--text" id="telegram">
              <v-icon>mdi-send-variant-outline</v-icon>
            </v-btn>
          </p>
        </v-col>
      </v-row>
    </footer>
</v-main>

</template>

