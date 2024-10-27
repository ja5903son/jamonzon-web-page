<template>
  <v-container>
    <h1 class="compras">Carrito de Compras</h1>
    <v-list>
      <v-list-item-group>
        <v-list-item
          v-for="(product, index) in cart"
          :key="index"
        >
          <v-list-item-content>
            <v-list-item-title>{{ product.title }}</v-list-item-title>
            <v-list-item-subtitle>{{ product.subtitle }}</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>
    <v-btn @click="goBack" class="back">Volver</v-btn>
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
