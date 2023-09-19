<template>
    <div class="flex flex-wrap">
<!-- RouterLink :to="{name: 'blogPost', params: {id: linkTitle(item.title) }}"  ------( Slug ba title ) link a dekhano   -->
        <RouterLink :to="{name: 'blogPost', params: {id: item.id }}" class="m-3 max-w-sm bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700" v-for="item in items.products" :key="item.id">
            <div >
                <img class="rounded-t-lg max-h-[10rem] min-w-[100%]" :src="`https://source.unsplash.com/random/300×300?${item.id}`" alt="" />
            </div>
            <div class="p-5">
                <div >
                    <h5 class="mb-2 text-2xl font-bold tracking-tight text-gray-900 dark:text-white">
                        {{ item.title }}
                    </h5>
                </div>
                <p class="mb-3 font-normal text-gray-700 dark:text-gray-400">
                    {{ item.description }}
                </p>
                <div 
                    class="inline-flex items-center px-3 py-2 text-sm font-medium text-center text-white bg-blue-700 rounded-lg hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800">
                    Read more
                    <svg class="w-3.5 h-3.5 ml-2" aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                        viewBox="0 0 14 10">
                        <path stroke="currentColor" stroke-linecap="round" stroke-linejoin="round" stroke-width="2"
                            d="M1 5h12m0 0L9 1m4 4L9 9" />
                    </svg>
                </div>
            </div>
        </RouterLink>
    </div>
</template>

<script setup>
import axios from 'axios';
import { ref, onMounted } from 'vue'
import { RouterLink } from 'vue-router';
const items = ref([])
onMounted( async () => {
    const url = 'https://dummyjson.com/products'
    const response = await axios.get(url)
    console.log(response.data.products)
    items.value = response.data
}) 

// ( Slug ba title ) link a dekhano
// function linkTitle(title){
//     return title.toLowerCase().replace( /\s+/g, '-')
// }
</script>

<style scoped></style>
