<template>
  <div class="card pb-0 px-0">
    <!-- 貼文標題 -->
    <div class="flex px-4">
      <div class="w-[44px] rounded-full overflow-hidden mr-3">
        <img src="https://bruce-fe-fb.web.app/image/avator.png" alt="avator" />
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
        <img src="https://bruce-fe-fb.web.app/image/more.svg" alt="more" />
      </button>
    </div>
    <!-- 貼文內容 -->
    <p class="test-base text-gray-300 mt-3 px-4">手做蛋糕台中分店開幕囉！！</p>
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
            <img src="https://bruce-fe-fb.web.app/image/like.svg" alt="like" />
          </div>
          <p class="text-gray-400 text-sm pl-1.5">讚</p>
        </button>
        <button
          class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
        >
          <div class="w-[16px]">
            <img src="https://bruce-fe-fb.web.app/image/chat.svg" alt="chat" />
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
</template>
