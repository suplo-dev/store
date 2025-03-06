<template>
    <div class="container mx-auto py-6">
        <h2 class="text-xl font-bold mb-4">Sản phẩm nổi bật</h2>
        <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
            <div v-for="product in products" :key="product.id" class="border p-4 rounded-lg shadow-md">
                <img :src="product.image" alt="product.name" class="w-full h-40 object-cover mb-2">
                <h3 class="font-semibold">{{ product.name }}</h3>
                <p class="text-red-600 font-bold">{{ product.price }}</p>
                <button @click="addToCart(product)" class="bg-blue-500 text-white px-4 py-2 rounded mt-2 w-full">
                    Thêm vào giỏ
                </button>
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref } from "vue";

const products = ref([
    { id: 1, name: "iPhone 15", price: "22.990.000₫", image: "/iphone15.jpg" },
    { id: 2, name: "Samsung S23", price: "19.490.000₫", image: "/samsung23.jpg" },
    { id: 3, name: "MacBook Air M2", price: "27.990.000₫", image: "/macbook.jpg" },
    { id: 4, name: "iPad Pro M2", price: "28.990.000₫", image: "/ipad.jpg" },
]);

const addToCart = (product) => {
    console.log("Thêm vào giỏ hàng:", product.name);
};
</script>
