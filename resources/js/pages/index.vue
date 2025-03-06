<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import {
    NavigationMenu,
    NavigationMenuContent,
    NavigationMenuItem,
    NavigationMenuLink,
    NavigationMenuList,
    NavigationMenuTrigger
} from '@/components/ui/navigation-menu';
import { Carousel, CarouselContent, CarouselItem, CarouselNext, CarouselPrevious } from '@/components/ui/carousel';

const menuItems = ['BỒN CẦU', 'LAVABO', 'SEN VÒI', 'PHỤ KIỆN', 'BỒN TẮM', 'BỘ SƯU TẬP'];
const components: { title: string, href: string, description: string }[] = [
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    },
    {
        title: 'Bồn cầu thông minh',
        href: '/docs/components/alert-dialog',
        description:
            'A modal dialog that interrupts the user with important content and expects a response.'
    }

];
import {
    Card,
    CardContent,
    CardDescription,
    CardFooter,
    CardHeader,
    CardTitle,
} from '@/components/ui/card'
</script>

<template>
    <Head title="Kuto">
        <link rel="preconnect" href="https://rsms.me/" />
        <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />
    </Head>
    <header class="bg-white shadow-md">
        <div class="container mx-auto px-4 py-3">
            <div class="flex items-center justify-between">
                <!-- Logo -->
                <div class="flex items-center space-x-2">
                    <!--                <img src="/logo.png" alt="Logo" class="h-10">-->
                    <span class="text-2xl font-bold text-gray-800">KUTO</span>
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
                        <span v-if="cartCount > 0"
                              class="absolute -top-2 -right-2 bg-red-500 text-white text-xs px-2 py-1 rounded-full">
            {{ cartCount }}
          </span>
                    </button>
                    <button @click="goToProfile">
                        👤
                    </button>
                </div>
            </div>
            <NavigationMenu class="mt-2 ml-20">
                <NavigationMenuList>
                    <NavigationMenuItem v-for="n in 7">
                        <NavigationMenuTrigger>BỒN CẦU</NavigationMenuTrigger>
                        <NavigationMenuContent>
                            <ul class="grid w-[700px] gap-3 p-4 md:w-[800px] md:grid-cols-2 lg:w-[900px] ">
                                <li v-for="component in components" :key="component.title">
                                    <NavigationMenuLink as-child>
                                        <a
                                            :href="component.href"
                                            class="block select-none space-y-1 rounded-md p-3 leading-none no-underline outline-none transition-colors hover:bg-accent hover:text-accent-foreground focus:bg-accent focus:text-accent-foreground"
                                        >
                                            <div class="text-sm font-medium leading-none">{{ component.title }}</div>
                                            <!--                                            <p class="line-clamp-2 text-sm leading-snug text-muted-foreground">-->
                                            <!--                                                {{ component.description }}-->
                                            <!--                                            </p>-->
                                        </a>
                                    </NavigationMenuLink>
                                </li>
                            </ul>
                        </NavigationMenuContent>
                    </NavigationMenuItem>
                </NavigationMenuList>
            </NavigationMenu>
        </div>

    </header>
    <!-- Main Section -->
    <div class="main">
        <div class="container mx-auto px-4 py-3">
            <div class="flex">
                <Carousel class="relative w-3/5">
                    <CarouselContent>
                        <CarouselItem v-for="(banner, index) in 4" :key="index">
                            <Card>
                                <CardContent class="flex items-center justify-center p-0">
                                    <img class="object-cover w-full" :src="`/img/${banner}.jpg`" alt="">
                                </CardContent>
                            </Card>
                        </CarouselItem>
                    </CarouselContent>
                    <CarouselPrevious />
                    <CarouselNext />
                </Carousel>
                <div class="w-1/5 mx-auto space-y-8">
                    <img class="object-cover w-10/12" src="/img/1.jpg" alt="">
                    <img class="object-cover w-10/12" src="/img/2.jpg" alt="">
                    <img class="object-cover w-10/12" src="/img/3.jpg" alt="">
                </div>
            </div>

            <Carousel
                class="relative w-full my-12"
                :opts="{align: 'start',}"
            >
                <CarouselContent>
                    <CarouselItem v-for="(_, index) in 10" :key="index" class="md:basis-1/2 lg:basis-1/5">
                        <div class="p-1">
                            <Card class="border-0">
                                <CardContent class="aspect-square p-0 w-32 m-auto">
                                    <img class="w-64 rounded-full object-cover" src="/img/product.png" alt="">
                                    <div class="text-center font-bold text-2xl">Bồn Cầu</div>
                                </CardContent>
                            </Card>
                        </div>
                    </CarouselItem>
                </CarouselContent>
                <CarouselPrevious />
                <CarouselNext />
            </Carousel>
            <div class="text-center text-3xl font-bold my-4">Sản phẩm tiêu biểu</div>
            <Carousel
                class="relative w-full"
                :opts="{align: 'start',}"
            >
                <CarouselContent>
                    <CarouselItem v-for="(_, index) in 10" :key="index" class="md:basis-1/2 lg:basis-1/5">
                        <div class="p-1">
                            <Card class="border-0">
                                <CardContent class="aspect-square p-0 w-64 m-auto">
                                    <img class="w-64" src="/img/product.png" alt="">
                                    <div class="text-center font-bold">Bồn Cầu 1 Khối Cao Cấp BALLY BL108N</div>
                                    <div class="text-center text-green-700">6,895,000₫</div>
                                </CardContent>
                            </Card>
                        </div>
                    </CarouselItem>
                </CarouselContent>
                <CarouselPrevious />
                <CarouselNext />
            </Carousel>
            <div class="text-center text-3xl font-bold my-4">Hàng mới về </div>
            <Carousel
                class="relative w-full"
                :opts="{align: 'start',}"
            >
                <CarouselContent>
                    <CarouselItem v-for="(_, index) in 10" :key="index" class="md:basis-1/2 lg:basis-1/5">
                        <div class="p-1">
                            <Card class="border-0">
                                <CardContent class="aspect-square p-0 w-64 m-auto">
                                    <img class="w-64" src="/img/product.png" alt="">
                                    <div class="text-center font-bold">Bồn Cầu 1 Khối Cao Cấp BALLY BL108N</div>
                                    <div class="text-center text-green-700">6,895,000₫</div>
                                </CardContent>
                            </Card>
                        </div>
                    </CarouselItem>
                </CarouselContent>
                <CarouselPrevious />
                <CarouselNext />
            </Carousel>
            <div class="text-center text-3xl font-bold my-4">Bán chạy</div>
            <Carousel
                class="relative w-full"
                :opts="{align: 'start',}"
            >
                <CarouselContent>
                    <CarouselItem v-for="(_, index) in 10" :key="index" class="md:basis-1/2 lg:basis-1/5">
                        <div class="p-1">
                            <Card class="border-0">
                                <CardContent class="aspect-square p-0 w-64 m-auto">
                                    <img class="w-64" src="/img/product.png" alt="">
                                    <div class="text-center font-bold">Bồn Cầu 1 Khối Cao Cấp BALLY BL108N</div>
                                    <div class="text-center text-green-700">6,895,000₫</div>
                                </CardContent>
                            </Card>
                        </div>
                    </CarouselItem>
                </CarouselContent>
                <CarouselPrevious />
                <CarouselNext />
            </Carousel>
        </div>
    </div>
</template>
