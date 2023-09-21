<script setup>
const props = defineProps(['gallery'])

</script>

<template>
    <Swiper :modules="[SwiperAutoplay, SwiperEffectCreative]" :slides-per-view="'auto'" :spaceBetween="10" :loop="true" :autoplay="{
         delay: 3000,
    disableOnInteraction: false,
    pauseOnMouseEnter: true
    }" class="h-full">
        <SwiperSlide class="h-full" v-for="( image, index ) in  gallery " :key="index">


            <img class="block max-h-full" :src="image.image.url" alt="">

        </SwiperSlide>
    </Swiper>
</template>

<style>
.swiper-wrapper {
    transition-timing-function: linear;
}
</style>