<script setup>
import { ref, onMounted } from 'vue';
import axios from 'axios';
import CategoryCard from '@/components/CategoryCard.vue';

const categories = ref([
    // { id: 1, title: "Mobile UI Kit", image: "categories-1.jpg", count: 731 },
    // { id: 2, title: "Fonts", image: "categories-2.jpg", count: 657 },
    // { id: 3, title: "Icon Set", image: "categories-3.jpg", count: 83559 },
    // { id: 4, title: "Website UI Kit", image: "categories-4.jpg", count: 4500 },
])

async function getCategoriesAPI() {
    try {
        const response = await axios.get('https://zullkit-backend.buildwithangga.id/api/categories?limit=400')
        // console.log(response.data)
        categories.value = response.data.data.data
    } catch (error) {
        console.error(error)
    }
}

onMounted(() => 
    getCategoriesAPI()
)
</script>

<template>
    <div class="container px-4 mx-auto my-16 md:px-12" id="categories">
        <h2 class="mb-4 text-xl font-medium md:mb-0 md:text-lg">All Categories</h2>
        <div class="flex flex-wrap -mx-1 lg:-mx-4">
            <CategoryCard 
                v-for="category in categories" 
                :key="category.id" 
                :id="category.id"
                :title="category.name" 
                :image="category.thumbnails" 
                :count="category.products_count" />

        </div>
    </div>
</template>