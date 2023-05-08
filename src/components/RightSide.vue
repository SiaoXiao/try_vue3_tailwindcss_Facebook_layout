<template>
  <div class="hidden sticky top-main-span max-w-[360px] w-full h-full lg:block">
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
</template>

<script setup></script>
