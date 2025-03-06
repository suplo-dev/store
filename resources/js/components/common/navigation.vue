<template>
    <nav class="bg-red-600 text-white py-2">
        <div class="container mx-auto flex items-center justify-between">
            <ul class="flex space-x-6">
                <li v-for="(item, index) in menuItems" :key="index" class="hover:underline cursor-pointer">
                    {{ item }}
                </li>
            </ul>
        </div>
    </nav>
</template>

<script setup>
const menuItems = ["Điện thoại", "Laptop", "Tablet", "Phụ kiện", "Khuyến mãi", "Tin tức"];
</script>
