<script setup lang="ts">
const prismic = usePrismic();
const { data: page } = useAsyncData("[homepage]", () =>
    prismic.client.getSingle("homepage")
);
const openEvent = ref(null);
function enter(element: any) {
    const width = getComputedStyle(element).width;
    element.style.width = width;
    element.style.position = "absolute";
    element.style.visibility = "hidden";
    element.style.height = "auto";
    const height = getComputedStyle(element).height;
    element.style.width = null;
    element.style.position = null;
    element.style.visibility = null;
    element.style.height = 0;
    getComputedStyle(element).height;
    requestAnimationFrame(() => {
        element.style.height = height;
    });
}
function afterEnter(element: any) {
    element.style.height = "auto";
}
function leave(element: any) {
    const height = getComputedStyle(element).height;
    element.style.height = height;
    getComputedStyle(element).height;
    requestAnimationFrame(() => {
        element.style.height = 0;
    });
}
function open(index: any) {
    openEvent.value = index;
    setTimeout(() => {
        document.getElementById('event-' + index)?.scrollIntoView({ behavior: 'smooth' });
    }, 800)
}

function shuffleArray(array) {
  for (let i = array.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [array[i], array[j]] = [array[j], array[i]];
  }
}
const showGallery = ref(false);
function openGallery() {

    const array = document.querySelectorAll('.gallery-img');
const images = Array.from(array);

// Shuffle the array
shuffleArray(images);

 



    const container = document.getElementById('gallery-wrapper');
    const containerWidth = container.offsetWidth;
    const containerHeight = container.offsetHeight;

    document.body.style.overflow = 'hidden';

    for (var i = 0; i < images.length; i++) {
        (function (i) {
            setTimeout(function () {
                let imgWidth = images[i].offsetWidth;
                let imgHeight = images[i].offsetHeight;

                // Calculate random positions within the container
                let maxX = containerWidth - imgWidth;
                let maxY = containerHeight - imgHeight;
                let newLeft = Math.random() * maxX;
                let newTop = Math.random() * maxY;

                images[i].style.left = newLeft + 'px';
                images[i].style.top = newTop + 'px';
                images[i].style.opacity = '1';
                images[i].style.zIndex = '10' + i;
            }, 1000 * i);
        })(i);
    }
}

useHead({
    title: 'Lutzival | 16.11—19.11.23',
    meta: [
        { name: 'description', content: 'Lutzival | 16.11—19.11.23' }
    ],
})
useSeoMeta({
    title: 'Lutzival | 16.11—19.11.23',
    ogTitle: 'Lutzival | 16.11—19.11.23',
    description: 'Various Locations, Berlin.',
    ogDescription: 'Various Locations, Berlin.',
    ogImage: './banner.jpg',
})
</script>

<template>
    <main class="h-full w-full">
        <!-- Header -->
        <section class="w-full flex flex-col items-center justify-center p-3">
            <!-- logo -->
            <div class="w-full md:w-5/6 p-5 md:p-10 mt-20 md:mt-10 relative">
                <svg viewBox="0 0 985 373" fill="none" xmlns="http://www.w3.org/2000/svg">
                    <path d="M54.6387 -3.05176e-05V332H110.139V373H0.138672V-3.05176e-05H54.6387Z" fill="#D9D9D9" />
                    <path
                        d="M170.838 -3.05176e-05V332H190.338V-3.05176e-05H244.338V346.5C244.338 354.167 241.671 360.5 236.338 365.5C231.005 370.5 224.505 373 216.838 373H143.338C135.671 373 129.338 370.5 124.338 365.5C119.338 360.5 116.838 354.167 116.838 346.5V-3.05176e-05H170.838Z"
                        fill="#D9D9D9" />
                    <path d="M252.58 40V-3.05176e-05H390.58V40H348.58V373H294.58V40H252.58Z" fill="#D9D9D9" />
                    <path
                        d="M393.693 373V332C393.693 320.667 395.527 306.667 399.193 290C403.193 273 407.86 254.833 413.193 235.5C418.86 216.167 425.027 196.5 431.693 176.5C438.36 156.5 444.36 137.5 449.693 119.5C455.36 101.5 460.027 85.5 463.693 71.5C467.693 57.5 469.693 47 469.693 40H398.193V-3.05176e-05H525.193V40C525.193 47 523.36 57.5 519.693 71.5C516.027 85.5 511.36 101.5 505.693 119.5C500.027 137.5 494.027 156.5 487.693 176.5C481.36 196.5 475.36 216.167 469.693 235.5C464.027 254.833 459.36 273 455.693 290C452.027 306.667 450.193 320.667 450.193 332H531.693V373H393.693Z"
                        fill="#D9D9D9" />
                    <path d="M594.189 373H539.689V-3.05176e-05H594.189V373Z" fill="#D9D9D9" />
                    <path
                        d="M600.689 -3.05176e-05H653.689L674.189 281L695.189 -3.05176e-05H748.189L708.189 373H640.189L600.689 -3.05176e-05Z"
                        fill="#D9D9D9" />
                    <path
                        d="M759.818 -3.05176e-05H827.818L867.818 373H814.818L808.818 286.5H778.818L773.318 373H720.318L759.818 -3.05176e-05ZM806.318 246.5L793.818 57L781.318 246.5H806.318Z"
                        fill="#D9D9D9" />
                    <path d="M928.662 -3.05176e-05V332H984.162V373H874.162V-3.05176e-05H928.662Z" fill="#D9D9D9" />
                </svg>
                <img @click="openGallery" class="sticker transition absolute top-0 right-0 w-[15%] h-auto z-50"
                    src="~/assets/lutz_sticker.png" alt="">

            </div>
            <!-- Gallery -->
            <section id="gallery-wrapper"
                class="fixed top-0 bottom-0 left-0 right-0 w-full height-0 select-none pointer-events-none z-10">
                <div class="relative h-full w-full pointer-events-none">


                    <img v-for="(image, index) in page?.data.gallery" :srcset="`
                    ${image.image.url}&w=600&fit=crop 1280w,
                                                                                ${image.image.url}&w=5&fit=crop 1024w,
                                                                                ${image.image.url}&w=400&fit=crop 768w,
                             `" :src="`${image.image.url}?w=200&fit=crop`" sizes="(min-width: 768w) 33.3vw, 100vw"
                        class="w-2/3 md:w-1/3 absolute gallery-img pointer-events-none drop-shadow-lg" alt="">
                </div>
            </section>

            <!-- Subheader -->
            <div class="w-full pb-20">
                <h2 class="text-secondary text-center ">
                    Various Locations, Berlin <svg
                        class="w-5 h-5 -translate-y-1 text-secondary dark:text-white inline-block" aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 17 21">
                        <g stroke="#747273" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.7">
                            <path d="M8 12a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z" />
                            <path
                                d="M13.8 12.938h-.01a7 7 0 1 0-11.465.144h-.016l.141.17c.1.128.2.252.3.372L8 20l5.13-6.248c.193-.209.373-.429.54-.66l.13-.154Z" />
                        </g>
                    </svg>
                </h2>
                <h1 class="text-primary text-center header-text font-bold">
                    16.11—19.11.23
                </h1>
            </div>
        </section>
        <!-- Content -->
        <section>
            <div :id="'event-' + index" @click="open(index)" v-for="(event, index) in page?.data.events" :key="index"
                :style="'background-color: rgba(217, 217, 217,' + (index + 1) / 10 + '1)'" class="hover:cursor-pointer">
                <div class="p-5">
                    <!-- header -->
                    <div class="py-10 text-center">
                        <div class="text-primary font-thin"> {{ event.title }}</div>
                        <div class="text-primary transition font-bold" :class="[openEvent === index ? 'opacity-0' : '']"> {{
                            event.short_date }}</div>
                    </div>

                    <!-- Details -->
                    <transition name="expand" @enter="enter" @after-enter="afterEnter" @leave="leave">

                        <div v-if="openEvent === index" class="py-10 text-center text-primary flex flex-col items-center"
                            :class="[openEvent === index ? 'border-t border-primary' : '']">
                            <div class="md:w-3/4">


                                <PrismicRichText class="header-text py-10 font-bold" :field="event.long_date" />
                                <PrismicRichText class="font-thin pb-10" :field="event.details" />
                                <div>
                                    <PrismicRichText class="font-thin pb-10 underline inline-block hover:cursor-pointer"
                                        :field="event.location" /> <span>
                                        <svg class="w-6 h-6 -translate-y-1 text-primary dark:text-white inline-block"
                                            aria-hidden="true" xmlns="http://www.w3.org/2000/svg" fill="none"
                                            viewBox="0 0 17 21">
                                            <g stroke="#D9D9D9" stroke-linecap="round" stroke-linejoin="round"
                                                stroke-width="1.7">
                                                <path d="M8 12a3 3 0 1 0 0-6 3 3 0 0 0 0 6Z" />
                                                <path
                                                    d="M13.8 12.938h-.01a7 7 0 1 0-11.465.144h-.016l.141.17c.1.128.2.252.3.372L8 20l5.13-6.248c.193-.209.373-.429.54-.66l.13-.154Z" />
                                            </g>
                                        </svg></span>
                                </div>
                                <p class="font-thin pb-10">{{ event.cap }}</p>

                                <div class="w-full flex justify-center">
                                    <a target="_blank" :href="event.form_link.url">
                                        <div
                                            class=" bg-primary text-[black] w-[15rem] rounded-full  border border-primary py-1 hover:bg-transparent transition hover:text-primary hover:cursor-pointer">
                                            Sign-Up</div>
                                    </a>
                                </div>
                            </div>
                        </div>
                    </transition>

                </div>
            </div>
        </section>
    </main>
</template>

<style>
.sticker {
    filter: drop-shadow(5px 5px 5px #222);
}


.gallery-img {
    opacity: 0;
    transform-origin: 0 0;
}


.overlay-img {
    position: absolute;
    top: 0;
    bottom: 0;
    height: 100%;
    width: 100%;
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}

.sticker:hover {
    transform: scale(1.1);
    cursor: pointer;
}

.expand-leave-active,
.expand-enter-active {
    transition: all 0.5s ease;
    overflow: hidden;
}

.expand-enter,
.expand-leave-to {
    height: 0;
    /* opacity: 0; */
}
</style>