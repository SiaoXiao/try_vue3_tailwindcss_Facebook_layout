<template>
  <div
    class="hidden sticky top-main-span max-w-[360px] pl-4 w-full h-full lg:block"
  >
    <div
      v-for="item in leftData"
      :key="item.text"
      class="flex items-center justify-items-center w-full p-2 mb-1 rounded hover:bg-fb-input cursor-pointer"
    >
      <div class="w-[32px] overflow-hidden rounded-full mr-4">
        <img :src="item.imgUrl" alt="avator" />
      </div>
      <p class="text-white text-[.9rem]">{{ item.text }}</p>
    </div>
  </div>
</template>

<script setup>
import { reactive, onMounted } from "vue";

const leftData = reactive([
  {
    text: "使用者",
    imgUrl: "https://bruce-fe-fb.web.app/image/avator.png",
  },
  {
    text: "活動",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/activity.svg",
  },
  {
    text: "天氣",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/cloudy.png",
  },
  {
    text: "災害應變中心",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/dynamic.svg",
  },
  {
    text: "新冠病毒資訊中心",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/facemask.svg",
  },
  {
    text: "社團",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/friend.svg",
  },
  {
    text: "企業管理平台",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/job.png",
  },
  {
    text: "Messenger",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/messenger.svg",
  },
  {
    text: "近期廣告動態",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/pay.png",
  },
  {
    text: "朋友名單",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/sale.png",
  },
  {
    text: "最愛",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/star.svg",
  },
  {
    text: "Marketplace",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/store.svg",
  },
  {
    text: "Watch",
    imgUrl: "https://bruce-fe-fb.web.app/image/left/watchingTv.svg",
  },
]);
</script>
