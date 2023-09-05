<template>
  <div
    class="mt-6 grid grid-cols-1 gap-x-6 gap-y-10 sm:grid-cols-2 lg:grid-cols-4 xl:gap-x-8"
  >
    <Item v-for="(product, index) in products"
      :key="index" :product="product"/>

  </div>
</template>

<script lang="ts">
import type { Product } from '../types/product.ts';
import { ref, onMounted } from "vue";
import Item from "./Item.vue";


export default {
  setup() {
    const products = ref<Product[]>([]);

    const fetchProducts = async () => {
      const response = await fetch(
        "https://fakestoreapi.com/products?limit=20",
      );
      const data = await response.json();
      products.value = data;
    };


    onMounted(() => {
      fetchProducts();
    });

    return {
      fetchProducts,
      products
    };
  },
  components: {
    Item,
  },
};
</script>
