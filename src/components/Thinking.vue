<template>
  <div class="rounded-lg mt-4 px-4 py-3 bg-fb-card">
    <div class="flex pb-4">
      <div class="w-[40px] rounded-full overflow-hidden mr-3 cursor-pointer">
        <img src="https://bruce-fe-fb.web.app/image/avator.png" alt="avator" />
      </div>
      <div
        class="bg-fb-input flex-1 rounded-full flex items-center cursor-pointer hover:bg-zinc-700"
      >
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
          <img src="https://bruce-fe-fb.web.app/image/photo.svg" alt="photo" />
        </div>
        <p class="text-gray-400 text-base font-semibold pl-1.5">相片 / 影片</p>
      </button>
      <button
        class="flex-1 h-[40px] rounded-lg hover:bg-fb-input flex items-center justify-center"
      >
        <div class="w-[24px]">
          <img src="https://bruce-fe-fb.web.app/image/feel.svg" alt="feel" />
        </div>
        <p class="text-gray-400 text-base font-semibold pl-1.5">感受 / 活動</p>
      </button>
    </div>
  </div>
</template>
