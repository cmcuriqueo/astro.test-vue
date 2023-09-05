<template>
    <div class="group relative bg-gray-200 rounded-md">
        <div
            class="aspect-h-1 aspect-w-1 w-full overflow-hidden rounded-md lg:aspect-none group-hover:opacity-75 lg:h-80 p-2">
            <img :src="product.image" :alt="product.title"
                class="h-full w-full object-cover object-center lg:h-full lg:w-full rounded-md" />
        </div>
        <div class="mt-4 flex justify-between  p-2">
            <div>
                <h3 class="text-sm text-gray-700 font-bold md:min-h-[70px]">
                    <a href="#">
                        <span aria-hidden="true" class="absolute inset-0"></span>
                        {{ truncate(product.title, 20) }}
                    </a>
                </h3>
                <p class="mt-1 text-sm text-gray-500 md:min-h-[90px]">{{ truncate(product.description) }}</p>

                <p class="mt-1 flex items-baseline justify-center gap-x-2">
                    <span class="text-2xl font-bold tracking-tight text-gray-900">${{ product.price }}</span>
                    <span class="text-sm font-semibold leading-6 tracking-wide text-gray-600">USD</span>
                </p>
                <a href="#"
                    class="mt-4 block w-full rounded-md bg-indigo-600 px-3 py-2 text-center text-sm font-semibold text-white shadow-sm hover:bg-indigo-500 focus-visible:outline focus-visible:outline-2 focus-visible:outline-offset-2 focus-visible:outline-indigo-600">Get
                    access
                </a>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import type { Product } from '../types/product.ts';
export default {
    props: {
        product: {
            type: Object as () => Product,
            required: true,
        }
    },
    methods: {
        truncate(text: string, length: number = 100 ) {
            return text.length > 100 ? text.substring(0, length) + "..." : text;
        }
    }
}

</script>