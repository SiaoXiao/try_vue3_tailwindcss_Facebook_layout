<template>
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
        <img src="https://bruce-fe-fb.web.app/image/search.svg" alt="search" />
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
        <div class="bg-fb-input rounded-full py-1 px-3 flex items-center mb-4">
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
</template>

<script setup>
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

const init = onMounted(() => {
  window.addEventListener("click", function () {
    handleOpenMenu("all", null);
  });
});
</script>

<style></style>
