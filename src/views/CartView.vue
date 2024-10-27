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
          <v-btn rounded="xl" size="x-small" color="red darken-3" elevation="0">
            <v-icon>mdi-close</v-icon>
          </v-btn>
        </v-list-item>
      </v-list-item-group>
    </v-list>
    <div class="d-flex justify-end mt-4">
      <v-btn @click="goBack" class="back">Volver</v-btn>
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

const props = defineProps(['cart']);
const router = useRouter();

const goBack = () => {
  router.push('/');
};
</script>
