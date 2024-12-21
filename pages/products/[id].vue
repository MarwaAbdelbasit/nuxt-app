<template>
    <div>
        <Head>
            <Title>{{ product.title }} | Nuxt Dojo</Title>
            <Meta name="description" :content="product.description" />
        </Head>

        <ProductDetails :product="product"></ProductDetails>
    </div>
</template>

<script setup>
    // [id] must match the file name
    const { id } = useRoute().params;
    const uri = `https://fakestoreapi.com/products/${id}`

    const { data: product } = await useFetch(uri);

    if(!product.value) {
        throw createError({
            statusCode: 404,
            statusMessage: 'Product not found',
            fatal: true // to fire an error also when it happens in the browser
        })
    }
    
    definePageMeta({
        layout: 'products'
    })
</script>

<style scoped>

</style>