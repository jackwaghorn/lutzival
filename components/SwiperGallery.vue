<script setup>
const props = defineProps(['gallery'])

</script>

<template>
    <div id="gallery" class="h-full w-full max-h-auto">
        <Swiper :modules="[SwiperAutoplay, SwiperEffectCreative]" :slides-per-view="'auto'" :loop="true" :autoplay="{
            delay: 4000,
            disableOnInteraction: true,
        }" class="h-full w-full max-h-auto">
            <SwiperSlide v-for="( image, index ) in  gallery " :key="index">


                <img class=" top-0 bottom-0 absolute lg:h-full left-0 right-0 m-auto" :src="image.image.url" alt="">

            </SwiperSlide>
        </Swiper>
    </div>
</template>