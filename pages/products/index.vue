<template>
    <div class="grid grid-cols-4 gap-5">
        <div v-for="product in products" :key="product.id">
            <ProductCard :product="product"/>
        </div>
    </div>
</template>

<script setup>
definePageMeta({
    layout: 'products'
})

const { data: products } = await useFetch('https://fakestoreapi.com/products');

useHead({
    title: "Nuxt Dojo | Products"
})
</script>

<style scoped>

</style>