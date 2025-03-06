<template>
    <div class="relative w-full">
        <img :src="banners[currentBanner]" class="w-full h-60 object-cover">
        <button @click="prevBanner" class="absolute left-5 top-1/2 transform -translate-y-1/2 bg-gray-800 text-white p-2 rounded-full">◀</button>
        <button @click="nextBanner" class="absolute right-5 top-1/2 transform -translate-y-1/2 bg-gray-800 text-white p-2 rounded-full">▶</button>
    </div>
</template>

<script setup>
import { ref } from "vue";

const banners = [
    "/banner1.jpg",
    "/banner2.jpg",
    "/banner3.jpg",
];
const currentBanner = ref(0);

const prevBanner = () => {
    currentBanner.value = (currentBanner.value - 1 + banners.length) % banners.length;
};
const nextBanner = () => {
    currentBanner.value = (currentBanner.value + 1) % banners.length;
};
</script>
