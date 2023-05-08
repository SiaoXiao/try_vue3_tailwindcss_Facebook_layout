<script setup>
import HeaderBar from "./components/HeaderBar.vue";
import LeftSide from "./components/LeftSide.vue";
import RightSide from "./components/RightSide.vue";
import TimeLimitedNews from "./components/TimeLimitedNews.vue";
import Thinking from "./components/Thinking.vue";
import PostWallBlank from "./components/PostWallBlank.vue";
import PostWall from "./components/PostWall.vue";

// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// import required modules
import { Navigation } from "swiper";
// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import { reactive } from "vue";

const swiper_options = reactive({
  loop: false,
  slidesPerView: "auto", //解决最后一张切换到第一张中间的空白
  navigation: {
    nextElRef: ".swiper-button-next",
    prevElRef: ".swiper-button-prev",
  },
});
const modules = [Navigation];


</script>

<template>
  <div class="bg-[#1c1e21]">
    <HeaderBar />
    <main class="min-h-screen pt-main-span flex">
      <!-- 左側資訊欄 -->
      <LeftSide />
      <!-- 動態牆 -->
      <div class="max-w-[744px] w-full mx-auto px-4 pb-4">
        <!-- 限時動態 -->
        <TimeLimitedNews />
        <!-- 在想些什麼 -->
        <Thinking />
        <!-- 開包廂 -->
        <div class="card pr-0 flex">
          <swiper
            :loop="swiper_options.loop"
            :slidesPerView="swiper_options.slidesPerView"
            :spaceBetween="30"
            :navigation="swiper_options.navigation"
            :modules="modules"
            class="mySwiper"
          >
            <swiper-slide>
              <button
                class="mr-4 px-4 h-[40px] ring-2 ring-gray-600 flex items-center rounded-full focus:outline-none"
              >
                <div class="w-[24px]">
                  <img
                    src="https://bruce-fe-fb.web.app/image/video.svg"
                    alt="video"
                  />
                </div>
                <p class="ml-2 text-fb text-sm font-bold">建立包廂</p>
              </button></swiper-slide
            >
            <swiper-slide v-for="(item, i) in 20" :key="i">
              <div class="w-[55px]">
                <div class="relative w-[40px] cursor-pointer">
                  <div class="overflow-hidden rounded-full">
                    <img
                      src="https://bruce-fe-fb.web.app/image/avator.png"
                      alt="avator"
                    />
                  </div>
                  <div
                    class="w-[10px] h-[10px] rounded-full bg-green-500 absolute bottom-0 right-0 ring ring-gray-900"
                  ></div>
                </div></div
            ></swiper-slide>
          </swiper>
        </div>
        <!-- 貼文牆 -->
        <PostWall />
        <!-- 貼文牆 (Loading) -->
        <PostWallBlank />
      </div>
      <!-- 右側聯絡人 -->
      <RightSide />
    </main>
  </div>
</template>
