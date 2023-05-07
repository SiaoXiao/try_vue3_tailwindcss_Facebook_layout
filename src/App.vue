<script setup>
// Import Swiper Vue.js components
import { Swiper, SwiperSlide } from "swiper/vue";

// import required modules
import { Navigation } from "swiper";
// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import { reactive, onMounted } from "vue";

const panelSwitch = reactive([
  {
    text: "plusPanel",
    isOpen: false,
  },
  {
    text: "messengerPanel",
    isOpen: false,
  },
  {
    text: "notificationPanel",
    isOpen: false,
  },
  {
    text: "morePanel",
    isOpen: false,
  },
]);

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
const swiper_options = reactive({
  loop: false,
  slidesPerView: "auto", //解决最后一张切换到第一张中间的空白
  navigation: {
        nextElRef: ".swiper-button-next",
        prevElRef: ".swiper-button-prev",
      },
});
const  modules= [Navigation]
const handleOpenMenu = (val, event) => {
  if (event) {
    event.stopPropagation();
  }
  panelSwitch.forEach((item) => {
    if (item.text === val) {
      item.isOpen = true;
    } else {
      item.isOpen = false;
    }
  });
};

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

const init = onMounted(() => {
  window.addEventListener("click", function () {
    handleOpenMenu("all", null);
  });
});
</script>

<template>
  <div class="bg-[#1c1e21]">
    <header
      class="w-full h-[56px] bg-fb-header fixed top-0 left-0 right-0 flex items-center justify-between px-4 z-40"
    >
      <!-- header left -->
      <div class="flex items-center">
        <!-- FB logo -->
        <svg
          viewBox="0 0 36 36"
          class="fill-current text-fb"
          height="39"
          width="39"
        >
          <defs>
            <linearGradient x1="50%" x2="50%" y1="97.0782153%" y2="0%">
              <stop offset="0%" stop-color="#0062E0"></stop>
              <stop offset="100%" stop-color="#19AFFF"></stop>
            </linearGradient>
          </defs>
          <path
            d="M15 35.8C6.5 34.3 0 26.9 0 18 0 8.1 8.1 0 18 0s18 8.1 18 18c0 8.9-6.5 16.3-15 17.8l-1-.8h-4l-1 .8z"
          ></path>
          <path
            class="fill-current text-white"
            d="M25 23l.8-5H21v-3.5c0-1.4.5-2.5 2.7-2.5H26V7.4c-1.3-.2-2.7-.4-4-.4-4.1 0-7 2.5-7 7v4h-4.5v5H15v12.7c1 .2 2 .3 3 .3s2-.1 3-.3V23h4z"
          ></path>
        </svg>
        <!-- search bar (手機版)-->
        <button class="popover-btn lg:hidden">
          <img
            src="https://bruce-fe-fb.web.app/image/search.svg"
            alt="search"
          />
        </button>
        <!-- search bar (電腦版)-->
        <div
          class="bg-fb-input ml-2 py-2 px-3 w-[240px] rounded-full items-center hidden lg:flex"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="w-[18px] h-[18px] mr-2"
            fill="none"
            viewBox="0 0 24 24"
            stroke="#9ba3af"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
            />
          </svg>
          <input
            type="text"
            class="w-full bg-transparent text-white focus:outline-none"
            placeholder="搜尋 Facebook"
          />
        </div>
      </div>
      <!-- header right -->
      <div class="flex items-center relative">
        <button
          class="popover-btn"
          id="plus"
          @click.stop="handleOpenMenu('plusPanel', $event)"
        >
          <img src="https://bruce-fe-fb.web.app/image/plus.svg" alt="plus" />
        </button>
        <button
          class="popover-btn"
          id="messenger"
          @click.stop="handleOpenMenu('messengerPanel', $event)"
        >
          <img
            src="https://bruce-fe-fb.web.app/image/messenger.svg"
            alt="messenger"
          />
        </button>
        <button
          class="popover-btn"
          id="notification"
          @click.stop="handleOpenMenu('notificationPanel', $event)"
        >
          <img src="https://bruce-fe-fb.web.app/image/bell.svg" alt="bell" />
        </button>
        <button
          class="popover-btn"
          id="more"
          @click.stop="handleOpenMenu('morePanel', $event)"
        >
          <img src="https://bruce-fe-fb.web.app/image/down.svg" alt="down" />
        </button>
        <!-- 下拉選單1 plus -->
        <div
          class="popover-panel"
          :class="panelSwitch[0].isOpen ? '' : 'hidden'"
          id="plus-panel"
        >
          <p class="text-white mb-3 text-2xl">建立</p>
          <div
            class="flex items-center p-1 mb-2 hover:bg-fb-input rounded-lg cursor-pointer"
          >
            <div
              class="bg-fb-input rounded-full p-2 mr-2 flex justify-center items-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                width="22"
                height="22"
                viewBox="0 0 24 24"
                stroke="white"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"
                />
              </svg>
            </div>
            <div class="flex-1">
              <p class="text-sm text-white mb-[2px]">貼文</p>
              <p class="text-xs text-gray-400">在動態消息分享貼文</p>
            </div>
          </div>
        </div>
        <!-- 下拉選單2 messenger -->
        <div
          class="popover-panel"
          :class="panelSwitch[1].isOpen ? '' : 'hidden'"
          id="msg-panel"
        >
          <p class="text-white mb-3 text-2xl">Messenger</p>
          <div
            class="bg-fb-input rounded-full py-1 px-3 flex items-center mb-4"
          >
            <svg
              xmlns="http://www.w3.org/2000/svg"
              class="w-[18px] h-[18px] mr-2"
              fill="none"
              viewBox="0 0 24 24"
              stroke="#9ba3af"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
              />
            </svg>
            <input
              type="text"
              class="w-full bg-transparent focus:outline-none text-white"
              placeholder="搜尋 Messenger"
            />
          </div>
          <div
            class="flex items-center mb-2 p-2 rounded-lg hover:bg-fb-input cursor-pointer"
          >
            <div class="w-[50px] h-[50px] rounded-full overflow-hidden mr-3">
              <img
                src="https://bruce-fe-fb.web.app/image/avator.png"
                alt="avator"
                class="w-full object-cover"
              />
            </div>
            <div class="flex-1">
              <p class="text-base text-white mb-[2px]">使用者</p>
              <p class="text-sm text-gray-400">Tailwind!．1分鐘前</p>
            </div>
          </div>
        </div>
        <!-- 下拉選單3 notification -->
        <div
          class="popover-panel"
          :class="panelSwitch[2].isOpen ? '' : 'hidden'"
          id="notification-panel"
        >
          <p class="text-white mb-3 text-2xl">通知</p>
          <div
            class="flex items-center mb-2 p-2 rounded-lg hover:bg-fb-input cursor-pointer"
          >
            <div class="w-[50px] h-[50px] rounded-full overflow-hidden mr-3">
              <img
                src="https://bruce-fe-fb.web.app/image/avator.png"
                alt="avator"
                class="w-full object-cover"
              />
            </div>
            <div class="flex-1">
              <p class="text-base text-white mb-[2px]">使用者發佈了一門新課</p>
              <p class="text-sm text-fb">1分鐘前</p>
            </div>
          </div>
        </div>
        <!-- 下拉選單4 more -->
        <div
          class="popover-panel"
          :class="panelSwitch[3].isOpen ? '' : 'hidden'"
          id="more-panel"
        >
          <div
            class="flex items-center mb-2 p-2 rounded-lg hover:bg-fb-input cursor-pointer"
          >
            <div class="w-[50px] h-[50px] rounded-full overflow-hidden mr-3">
              <img
                src="https://bruce-fe-fb.web.app/image/avator.png"
                alt="avator"
                class="w-full object-cover"
              />
            </div>
            <div class="flex-1">
              <p class="text-base text-white mb-[2px]">使用者</p>
              <p class="text-sm text-gray-400">查看你個人檔案</p>
            </div>
          </div>
          <div
            class="flex p-1 mb-2 items-center hover:bg-fb-input rounded-lg cursor-pointer"
          >
            <div
              class="bg-fb-input rounded-full p-2 mr-2 flex justify-center items-center"
            >
              <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                width="22"
                height="22"
                viewBox="0 0 24 24"
                stroke="white"
              >
                <path
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  d="M17 16l4-4m0 0l-4-4m4 4H7m6 4v1a3 3 0 01-3 3H6a3 3 0 01-3-3V7a3 3 0 013-3h4a3 3 0 013 3v1"
                />
              </svg>
            </div>
            <p class="flex-1 text-white">登出</p>
          </div>
        </div>
      </div>
    </header>

    <main class="min-h-screen pt-main-span flex">
      <!-- 左側資訊欄 -->
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
      <!-- 動態牆 -->
      <div class="max-w-[744px] w-full mx-auto px-4 pb-4">
        <!-- 限時動態 -->
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
        <!-- 在想些什麼 -->
        <div class="rounded-lg mt-4 px-4 py-3 bg-fb-card">
          <div class="flex pb-4">
            <div class="w-[40px] rounded-full overflow-hidden mr-3 cursor-pointer">
              <img
                src="https://bruce-fe-fb.web.app/image/avator.png"
                alt="avator"
              />
            </div>
            <div class="bg-fb-input flex-1 rounded-full flex items-center cursor-pointer hover:bg-zinc-700">
              <p class="text-left text-base pl-3 text-gray-400">
                使用者，在想些什麼？
              </p>
            </div>
          </div>
          <div class="border-t border-gray-700 flex pt-3">
            <button
              class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
            >
              <div class="w-[24px]">
                <img
                  src="https://bruce-fe-fb.web.app/image/camera.svg"
                  alt="camera"
                />
              </div>
              <p class="text-gray-400 text-base font-semibold pl-1.5">直播視訊</p>
            </button>
            <button
              class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
            >
              <div class="w-[24px]">
                <img
                  src="https://bruce-fe-fb.web.app/image/photo.svg"
                  alt="photo"
                />
              </div>
              <p class="text-gray-400 text-base font-semibold pl-1.5">相片 / 影片</p>
            </button>
            <button
              class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
            >
              <div class="w-[24px]">
                <img
                  src="https://bruce-fe-fb.web.app/image/feel.svg"
                  alt="feel"
                />
              </div>
              <p class="text-gray-400 text-base font-semibold pl-1.5">感受 / 活動</p>
            </button>
          </div>
        </div>
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
        <div class="card pb-0 px-0">
          <!-- 貼文標題 -->
          <div class="flex px-4">
            <div class="w-[44px] rounded-full overflow-hidden mr-3">
              <img
                src="https://bruce-fe-fb.web.app/image/avator.png"
                alt="avator"
              />
            </div>
            <div class="flex-1">
              <p class="text-white">使用者名稱</p>
              <div class="flex items-center text-gray-400 text-sm">
                <div>5小時</div>
                <div>．</div>
                <div class="w-[12px]">
                  <img
                    src="https://bruce-fe-fb.web.app/image/earth.svg"
                    alt="earth"
                  />
                </div>
              </div>
            </div>
            <button class="w-[12px] focus:outline-none">
              <img
                src="https://bruce-fe-fb.web.app/image/more.svg"
                alt="more"
              />
            </button>
          </div>
          <!-- 貼文內容 -->
          <p class="test-base text-gray-300 mt-3 px-4">
            手做蛋糕台中分店開幕囉！！
          </p>
          <!-- 貼文圖片 -->
          <a href="#" class="block mt-3">
            <div class="w-full overflow-hidden h-[260px]">
              <img
                src="https://bruce-fe-fb.web.app/image/item.png"
                alt="item"
                class="object-cover w-full"
              />
            </div>
            <div class="bg-fb-input w-full px-4 py-2 text-white">
              <p class="text-gray-400 text-sm">www.Google.com</p>
              <p class="text-lg">手做蛋糕台中分店開幕囉！！</p>
            </div>
          </a>
          <!-- 讚、留言 -->
          <div class="px-4">
            <div class="border-b border-gray-700 flex justify-between py-3">
              <div class="flex items-center">
                <div class="w-[18px] mr-2">
                  <img
                    src="https://bruce-fe-fb.web.app/image/like-blue.svg"
                    alt="like blue"
                  />
                </div>
                <p class="text-sm text-gray-400">123</p>
              </div>
              <div class="flex items-center">
                <p class="text-sm text-gray-400 mr-2">4則留言</p>
                <p class="text-sm text-gray-400">1次分享</p>
              </div>
            </div>
            <div class="flex items-center py-2">
              <button
                class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
              >
                <div class="w-[16px]">
                  <img
                    src="https://bruce-fe-fb.web.app/image/like.svg"
                    alt="like"
                  />
                </div>
                <p class="text-gray-400 text-sm pl-1.5">讚</p>
              </button>
              <button
                class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
              >
                <div class="w-[16px]">
                  <img
                    src="https://bruce-fe-fb.web.app/image/chat.svg"
                    alt="chat"
                  />
                </div>
                <p class="text-gray-400 text-sm pl-1.5">留言</p>
              </button>
              <button
                class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
              >
                <div class="w-[16px]">
                  <img
                    src="https://bruce-fe-fb.web.app/image/share.svg"
                    alt="share"
                  />
                </div>
                <p class="text-gray-400 text-sm pl-1.5">分享</p>
              </button>
            </div>
          </div>
        </div>
        <!-- 貼文牆 (Loading) -->
        <div class="card pb-0 px-0 animate-pulse">
          <!-- 貼文標題 -->
          <div class="flex px-4 items-center mb-4">
            <div
              class="w-[44px] h-[44px] rounded-full overflow-hidden mr-3 bg-fb-input"
            ></div>
            <div class="flex content-evenly flex-wrap w-[200px] h-[50px]">
              <div class="bg-fb-input h-[16px] w-[200px] rounded-full"></div>
              <div class="bg-fb-input h-[12px] w-[100px] rounded-full"></div>
            </div>
          </div>
          <div class="w-full h-[260px] bg-fb-input"></div>
        </div>
      </div>
      <!-- 右側聯絡人 -->
      <div
        class="hidden sticky top-main-span max-w-[360px] w-full h-full lg:block"
      >
        <p class="mb-2 text-lg text-gray-400">聯絡人</p>
        <div
          v-for="(item, i) in 6"
          :key="i"
          class="flex items-center justify-items-center w-full py-2 px-1 rounded hover:bg-fb-input cursor-pointer"
        >
          <div class="w-[45px]">
            <div class="relative w-[32px] cursor-pointer">
              <div class="overflow-hidden rounded-full">
                <img
                  src="https://bruce-fe-fb.web.app/image/avator.png"
                  alt="avator"
                />
              </div>
              <div
                class="w-[8px] h-[8px] rounded-full bg-green-500 absolute bottom-0 right-0 ring-gray-900 ring"
              ></div>
            </div>
          </div>
          <p class="text-white text-[.9rem]">使用者</p>
        </div>
      </div>
    </main>
  </div>
</template>
