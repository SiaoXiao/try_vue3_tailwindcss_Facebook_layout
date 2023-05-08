<template>
  <div class="relative">
    <div class="flex overflow-x-auto no-scrollbar">
      <div class="flex-1 px-[4px] min-w-[120px] cursor-pointer">
        <div class="h-full flex flex-col">
          <div class="h-full overflow-hidden">
            <img
              src="https://bruce-fe-fb.web.app/image/avator.png"
              alt="avator"
              class="object-cover w-full h-full duration-500 hover:scale-105"
            />
          </div>
          <div class="bg-fb-card pt-6 px-2 pb-2 relative">
            <button
              class="w-[32px] h-[32px] p-2 absolute -top-4 left-[calc(50%-16px)] bg-fb rounded-full focus:outline-none ring-fb-card ring flex justify-center items-center"
            >
              <img
                src="https://bruce-fe-fb.web.app/image/plus.svg"
                alt="plus"
              />
            </button>
            <p class="w-full text-center text-white">建立限時動態</p>
          </div>
        </div>
      </div>

      <div
        class="flex-1 px-[4px] min-w-[120px] cursor-pointer"
        v-for="(item, i) in 9"
        :key="i"
        @mouseenter="handleScaleImg('in', $event)"
        @mouseleave="handleScaleImg('out', $event)"
      >
        <div class="relative overflow-hidden">
          <div
            class="hidden absolute w-full h-full top-0 left-0 bg-black/20 z-20"
          ></div>
          <div
            class="w-[32px] h-[32px] absolute top-4 left-4 ring-4 ring-fb bg-fb-active rounded-full flex justify-center items-center z-10"
          >
            <p class="text-white text-sm">U</p>
          </div>
          <div
            class="absolute w-full h-full top-0 left-0 bg-gradient-to-b from-black/30 to-transparent z-20"
          ></div>
          <img
            src="https://images.pexels.com/photos/1366919/pexels-photo-1366919.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
            alt="story"
            class="w-full h-full duration-500"
          />
          <p class="absolute bottom-2 left-2 text-white z-10">使用者</p>
        </div>
      </div>
    </div>
    <button
      class="absolute popover-btn -right-3 top-[calc(50%-22.5px)] z-30 w-[45px] h-[45px]"
    >
      <img
        src="https://bruce-fe-fb.web.app/image/right-arrow.svg"
        alt="right arrow"
      />
    </button>
  </div>
</template>

<script setup>
import { reactive, onMounted } from "vue";
const handleScaleImg = (val, event) => {
  const mask = event.target.childNodes[0].childNodes[0];
  const image = event.target.childNodes[0].childNodes[3];

  if (val === "in") {
    mask.classList.remove("hidden");
    image.classList.add("scale-105");
  } else {
    mask.classList.add("hidden");
    image.classList.remove("scale-105");
  }
};
</script>

<style></style>
