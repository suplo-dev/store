<template>
    <header class="bg-white shadow-md">
        <div class="container mx-auto px-4 py-3 flex items-center justify-between">
            <!-- Logo -->
            <div class="flex items-center space-x-2">
<!--                <img src="/logo.png" alt="Logo" class="h-10">-->
                <span class="text-lg font-bold text-gray-800">KUTO</span>
            </div>

            <!-- Thanh tìm kiếm -->
            <div class="flex-1 mx-4">
                <div class="relative">
                    <input
                        v-model="searchQuery"
                        type="text"
                        placeholder="Tìm kiếm sản phẩm..."
                        class="w-full px-4 py-2 border rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
                    />
                    <button
                        @click="searchProduct"
                        class="absolute right-2 top-1/2 transform -translate-y-1/2 text-gray-500"
                    >
                        🔍
                    </button>
                </div>
            </div>

            <!-- Icons: Giỏ hàng, Tài khoản -->
            <div class="flex items-center space-x-6">
                <button @click="goToCart" class="relative">
                    🛒
                    <span v-if="cartCount > 0" class="absolute -top-2 -right-2 bg-red-500 text-white text-xs px-2 py-1 rounded-full">
            {{ cartCount }}
          </span>
                </button>
                <button @click="goToProfile">
                    👤
                </button>
            </div>
        </div>
        <div class="container mx-auto px-4 py-3 flex items-center justify-between">
            <ul>

            </ul>
        </div>
    </header>
</template>

<script setup>
import { ref } from "vue";

const searchQuery = ref("");
const cartCount = ref(2); // Số lượng sản phẩm trong giỏ hàng (giả định)

const searchProduct = () => {
    console.log("Tìm kiếm:", searchQuery.value);
};

const goToCart = () => {
    console.log("Đi đến giỏ hàng");
};

const goToProfile = () => {
    console.log("Đi đến trang cá nhân");
};
</script>

<style scoped>
/* Thêm CSS tùy chỉnh nếu cần */
</style>
