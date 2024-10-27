<template>
  <v-container>
    <h1 class="compras text-center">Carrito de Compras</h1>
    <v-list>
      <v-list-item-group>
        <v-list-item
          v-for="(product, index) in cart"
          :key="index"
          class="d-flex justify-space-between align-center"
        >
          <v-list-item-content>
            <v-list-item-title>{{ product.title }}</v-list-item-title>
            <v-list-item-subtitle>{{ product.subtitle }}</v-list-item-subtitle>
          </v-list-item-content>
          <v-btn rounded="xl" size="x-small" color="red darken-3" elevation="0" @click="deleteItem(index)">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-list-item>
      </v-list-item-group>
    </v-list>
    <div class="d-flex justify-end mt-4">
      <v-btn rounded="lg" color="grey" @click="goBack" class="back">Volver</v-btn>
      <v-btn rounded="lg" color="green" @click="sendMessage"  class="back" >Comprar</v-btn>
    </div>
  </v-container>
</template>

<script setup>
import { defineProps } from 'vue';
import { useRouter } from 'vue-router';
import { ref } from 'vue';
import { useRoute } from 'vue-router';

const route = useRoute();
const cart = ref(JSON.parse(route.query.cart || '[]'));

const sendMessage = () => {
  const phoneNumber = '+5356098551'; // Reemplaza con el número de teléfono deseado
  const message = generateMessage(cart.value);
  
  const encodedMessage = encodeURIComponent(message);
  const url = `https://wa.me/${phoneNumber}?text=${encodedMessage}`;

  // Abre el enlace en una nueva ventana
  window.open(url, '_blank');
};

const generateMessage = (data) => {
  return data.map(item => `${item.title} - Precio: ${item.subtitle}`).join('\n');
};

const props = defineProps(['cart']);
const router = useRouter();

const goBack = () => {
  router.push('/');
};
const deleteItem = (index) => {
  cart.value.splice(index, 1); 
  
};
</script>
