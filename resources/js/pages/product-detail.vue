<script setup lang="ts">
import { Head, Link } from '@inertiajs/vue3';
import Autoplay from 'embla-carousel-autoplay';
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
    CardFooter,
    CardHeader,
    CardTitle
} from '@/components/ui/card';
import { onMounted, ref } from 'vue';
import { watchOnce } from '@vueuse/core';

const emblaMainApi = ref<CarouselApi>();
const emblaThumbnailApi = ref<CarouselApi>();
const selectedIndex = ref(0);

function onSelect() {
    if (!emblaMainApi.value || !emblaThumbnailApi.value)
        return;
    selectedIndex.value = emblaMainApi.value.selectedScrollSnap();
    emblaThumbnailApi.value.scrollTo(emblaMainApi.value.selectedScrollSnap());
}

function onThumbClick(index: number) {
    if (!emblaMainApi.value || !emblaThumbnailApi.value)
        return;
    emblaMainApi.value.scrollTo(index);
}

watchOnce(emblaMainApi, (emblaMainApi) => {
    if (!emblaMainApi)
        return;

    onSelect();
    emblaMainApi.on('select', onSelect);
    emblaMainApi.on('reInit', onSelect);
});
import {
    Breadcrumb,
    BreadcrumbEllipsis,
    BreadcrumbItem,
    BreadcrumbLink,
    BreadcrumbList,
    BreadcrumbPage,
    BreadcrumbSeparator
} from '@/components/ui/breadcrumb';
import {
    DropdownMenu,
    DropdownMenuContent,
    DropdownMenuItem,
    DropdownMenuTrigger
} from '@/components/ui/dropdown-menu';
</script>

<template>
    <Head title="Kuto">
        <!--        <link rel="preconnect" href="https://rsms.me/" />-->
        <!--        <link rel="stylesheet" href="https://rsms.me/inter/inter.css" />-->
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
            <Breadcrumb class="mb-2">
                <BreadcrumbList>
                    <BreadcrumbItem>
                        <BreadcrumbPage >Trang chủ</BreadcrumbPage>
                    </BreadcrumbItem>
                    <BreadcrumbSeparator  />
                    <BreadcrumbItem>
                        <BreadcrumbPage >Bồn cầu</BreadcrumbPage>
                    </BreadcrumbItem>
                    <BreadcrumbItem>
                        <BreadcrumbPage >Bồn cầu 1 khối</BreadcrumbPage>
                    </BreadcrumbItem>
                    <BreadcrumbSeparator />
                    <BreadcrumbItem>
                        <BreadcrumbPage >Bồn Cầu 1 Khối Cao Cấp BALLY BL108N</BreadcrumbPage>
                    </BreadcrumbItem>
                </BreadcrumbList>
            </Breadcrumb>
            <div class="flex">
                <Card class="w-full">
                    <CardContent class="flex">
                        <div class="w-1/3">
                            <Carousel
                                class="relative w-full"
                                @init-api="(val) => emblaMainApi = val"
                            >
                                <CarouselContent>
                                    <CarouselItem v-for="(_, index) in 10" :key="index">
                                        <Card>
                                            <CardContent class="flex aspect-square items-center justify-center p-0">
                                                <img class="w-full" src="/img/product.png" alt="">
                                            </CardContent>
                                        </Card>
                                    </CarouselItem>
                                </CarouselContent>
                                <CarouselPrevious />
                                <CarouselNext />
                            </Carousel>
                            <Carousel
                                class="relative w-full mt-2"
                                @init-api="(val) => emblaThumbnailApi = val"
                            >
                                <CarouselContent class="flex gap-1 ml-0">
                                    <CarouselItem v-for="(_, index) in 10" :key="index"
                                                  class="pl-0 basis-1/4 cursor-pointer" @click="onThumbClick(index)">
                                        <Card :class="index === selectedIndex ? '' : 'opacity-50'">
                                            <CardContent class="flex aspect-square items-center justify-center p-0">
                                                <img class="w-full object-contain" src="/img/product.png" alt="">
                                            </CardContent>
                                        </Card>
                                    </CarouselItem>
                                </CarouselContent>
                            </Carousel>
                        </div>
                        <div class="ml-24">
                            <div class=" text-2xl font-bold">
                                Bồn Cầu 1 Khối Cao Cấp BALLY BL108N
                            </div>
                            <hr class="my-2 mb-6">
                            <div class="text-blue-400 text-xl font-bold">Thông tin sản phẩm</div>
                            <ul class="ml-6 my-2" style="list-style-type: circle">
                                <li>Tên sản phẩm: Bồn cầu một khối H-BC269</li>
                                <li>Bồn cầu Luxury Class</li>
                                <li>Thiết kế hiện đại, sang trọng</li>
                                <li>Công nghệ GERMANY</li>
                                <li>Phụ kiện đồng bộ WDI</li>
                                <li>Kiểu xả: Xả xoáy Tornado Flush</li>
                                <li>Nắp đóng êm chuẩn EU</li>
                                <li>Kích thước: 670x390x700mm</li>
                            </ul>
                            <div class="text-blue-400 text-xl font-bold">HOTLINE: 19001900</div>
                        </div>
                    </CardContent>
                </Card>
            </div>
            <hr class="my-2 mb-6">
            <Card class="w-full">
                <CardContent class="flex">
                    <div>
                        <hr class="my-2 mb-6">
                        <div class="text-blue-400 text-xl font-bold">Mô tả sản phẩm</div>
                        <div class="mt-2">
                            <h3 class="text-xl font-bold text-gray-800">
                                Bồn cầu một khối H-BC269 – Sự lựa chọn đẳng cấp cho không gian sang trọng
                            </h3>
                            <p class="mt-2 text-gray-700">
                                Tạo nên một không gian vệ sinh sang trọng và hiện đại với Bồn cầu một khối H-BC269.
                                Được thiết kế với kiểu dáng tinh tế, sản phẩm này không chỉ mang lại sự tiện nghi
                                mà còn làm nổi bật phong cách sang trọng cho phòng tắm của bạn.
                            </p>

                            <!-- Video -->
                            <div class="mt-4">
                                <iframe loading="lazy" title="BỒN CẦU MỘT KHỐI HUGE H-BC269" width="1020" height="574" src="https://www.youtube.com/embed/eS71Rdzw81s?feature=oembed" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen=""></iframe>
                            </div>

                            <!-- Features -->
                            <div class="mt-6 space-y-4">
                                <div>
                                    <h3 class="text-xl font-semibold text-gray-800">🏛 Kiểu dáng sang trọng</h3>
                                    <p class="text-gray-700">Bồn cầu H-BC269 có thiết kế hiện đại, mang lại vẻ đẹp thanh lịch.</p>
                                </div>

                                <div>
                                    <h3 class="text-xl font-semibold text-gray-800">🔬 Công nghệ GERMANY</h3>
                                    <p class="text-gray-700">
                                        Sử dụng công nghệ men sứ cao cấp với lớp tráng kháng nước, giúp chống bám bẩn và dễ vệ sinh.
                                    </p>
                                </div>

                                <div>
                                    <h3 class="text-xl font-semibold text-gray-800">🛠 Phụ kiện đồng bộ WDI</h3>
                                    <p class="text-gray-700">
                                        Đạt tiêu chuẩn EU, đảm bảo độ bền cao và hiệu suất sử dụng vượt trội.
                                    </p>
                                </div>

                                <div>
                                    <h3 class="text-xl font-semibold text-gray-800">💦 Xả xoáy Tornado Flush</h3>
                                    <p class="text-gray-700">
                                        Công nghệ xả xoáy mạnh mẽ, giúp làm sạch hiệu quả.
                                    </p>
                                </div>

                                <div>
                                    <h3 class="text-xl font-semibold text-gray-800">🔇 Nắp đóng êm chuẩn EU</h3>
                                    <p class="text-gray-700">
                                        Chất liệu UF cao cấp với cơ chế đóng mở êm ái, không gây tiếng ồn.
                                    </p>
                                </div>

                                <div>
                                    <h3 class="text-xl font-semibold text-gray-800">📏 Kích thước lý tưởng</h3>
                                    <p class="text-gray-700">670x390x700mm, phù hợp với nhiều không gian phòng tắm.</p>
                                </div>
                            </div>

                            <p class="mt-6 text-gray-800 font-semibold">
                                Hãy nâng cấp không gian vệ sinh của bạn với bồn cầu Luxury Class H-BC269 và trải nghiệm sự khác biệt trong từng chi tiết.
                            </p>

                            <!-- Contact Info -->
                            <div class="mt-6 border-t pt-4">
                                <h4 class="text-lg font-semibold text-gray-800">📞 Thông tin liên hệ:</h4>
                                <ul class="mt-2 space-y-2 text-gray-700">
                                    <li><strong>Địa chỉ:</strong> Số 18 & 19 BT7 Foresa 6A KĐT Sinh Thái Xuân Phương, Nam Từ Liêm, Hà Nội</li>
                                    <li><strong>Điện thoại:</strong> <a href="tel:19000225" class="text-blue-600 hover:underline">1900 0225</a></li>
                                    <li><strong>Email:</strong> <a href="mailto:hugevina@gmail.com" class="text-blue-600 hover:underline">hugevina@gmail.com</a></li>
                                    <li><strong>Website:</strong> <a href="https://huge-germany.com/" target="_blank" class="text-blue-600 hover:underline">huge-germany.com</a></li>
                                </ul>
                            </div>

                            <!-- Social Media -->
                            <div class="mt-6 border-t pt-4">
                                <h4 class="text-lg font-semibold text-gray-800">🌍 Kết nối với chúng tôi:</h4>
                                <div class="flex space-x-4 mt-2">
                                    <a href="https://www.facebook.com/nhatamthongminhhuge19000225" target="_blank"
                                       class="text-blue-600 hover:underline">Facebook</a>
                                    <a href="https://www.youtube.com/@thietbiphukiennhatamthongminh" target="_blank"
                                       class="text-red-600 hover:underline">YouTube</a>
                                </div>
                            </div>
                        </div>

                    </div>
                </CardContent>
            </Card>
        </div>
    </div>
</template>
