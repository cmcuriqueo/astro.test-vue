<template>
  <div class="bg-white">
    <header class="relative bg-white">
      <p class="flex h-10 items-center justify-center bg-indigo-600 px-4 text-sm font-medium text-white sm:px-6 lg:px-8">
        Get free delivery on orders over $100
      </p>

      <nav aria-label="Top" class="mx-auto max-w-7xl px-4 sm:px-6 lg:px-8">
        <div class="border-b border-gray-200">
          <div class="flex h-16 items-center">
            <!-- Logo -->
            <div class="ml-4 flex lg:ml-0">
              <a href="#">
                <span class="sr-only">Your Company</span>
                <img class="h-8 w-auto" src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=600" alt="" />
              </a>
            </div>

            <!-- Flyout menus -->
            <div class="sm:ml-2 lg:ml-8 lg:block lg:self-stretch">
              <div class="flex h-full space-x-8">
                <a v-for="(category, index) in categories" :key="index" :href="`/category/${category}`"
                  class="flex items-center text-sm font-medium text-gray-700 hover:text-gray-800 uppercase">{{ category }}</a>
              </div>
            </div>
          </div>
        </div>
      </nav>
    </header>
  </div>
</template>

<script lang="ts">
import type { Category } from '../types/category.ts';
import { ref, onMounted } from "vue";
export default {
  setup() {
    const categories = ref<Category[]>([]);
    const fetchCategories = async () => {
      const response = await fetch(
        "https://fakestoreapi.com/products/categories",
      );
      const data = await response.json();

      console.log(data);
      categories.value = data;
    };


    onMounted(() => {
      fetchCategories();
    });

    return {
      categories,
      fetchCategories
    }
  }
}
</script>