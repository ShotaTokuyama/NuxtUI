<script setup>
const slides = ref(
  Array.from({ length: 10 }, () => {
    const r = Math.floor(Math.random() * 256);
    const g = Math.floor(Math.random() * 256);
    const b = Math.floor(Math.random() * 256);
    // Figure out contrast color for font
    const contrast =
      r * 0.299 + g * 0.587 + b * 0.114 > 186 ? "black" : "white";

    return { bg: `rgb(${r}, ${g}, ${b})`, color: contrast };
  })
);
</script>

<template>
  <Swiper
    :height="500"
    :modules="[
      SwiperAutoplay,
      SwiperEffectCreative,
      SwiperPagination,
      SwiperMousewheel,
      SwiperNavigation,
    ]"
    :slides-per-view="1"
    :loop="true"
    :effect="'creative'"
    :autoplay="{
      delay: 2000,
      disableOnInteraction: true,
    }"
    :creative-effect="{
      prev: {
        shadow: true,
        translate: ['-20%', 0, -1],
      },
      next: {
        shadow: true,
        translate: ['100%', 0, 0],
      },
    }"
    :pagination="true"
    :mousewheel="true"
    :navigation="true"
  >
    <SwiperSlide
      v-for="(slide, idx) in slides"
      :key="idx"
      :style="`background-color: rgb(203 213 225); color: rgb(71 85 105)`"
    >
      {{ idx }}
    </SwiperSlide>
  </Swiper>
</template>

<style>
.swiper-slide {
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 18px;
  height: 500px;
  font-size: 4rem;
  font-weight: bold;
  font-family: "Roboto", sans-serif;
}

.swiper-button-prev,
.swiper-button-next {
  color: rgb(71 85 105);
}
.swiper-pagination-bullet {
  background-color: rgb(71 85 105);
}
</style>
