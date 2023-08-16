<template>
  <div class="h-full p-4 pt-0 sm:p-4  flex justify-center">
    <div
      class="h-full sm:h-[76vh] text-center items-center justify-center text-[#144779] flex flex-col"
    >
      <p>QR CODE สำหรับลูกค้า</p>
      <img class="mt-4" src="../../assets/images/qr_test.png" />
      <button
        class="mt-4 flex items-center justify-between px-3 py-1 bg-[#144779] w-9/12 h-[5vh]  md:w-9/12 lg:w-9/12 rounded-[30px]"
      >
        <svg
          class="h-6 w-6 transform transition-transform duration-200 ease-in-out text-[#FFF]"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 16v1a3 3 0 003 3h10a3 3 0 003-3v-1m-4-4l-4 4m0 0l-4-4m4 4V4"
          />
        </svg>

        <span style="color: #fff; font-size: 16px"> บันทึกลงอุปกรณ์</span>
        <div></div>
      </button>
    </div>
  </div>
</template>
