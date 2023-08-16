<!-- Please remove this file from your project -->
<template>

  <div
    class="max-w-md mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-3xl"
  >
    <div class="md:flex">
      <div class="md:shrink-0 relative">
      <img class="h-80 w-full object-cover md:h-full md:w-96" src="../assets/images/imglogin.svg" />
      <div class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-center">
        <div class="text-left ">
            <span class="text-white text-6xl ">Welcome</span><br />
            <span class="text-white text-xl font-extralight"
              >To Parking Dashboard</span
            ><br />
            <div class="bg-white col-span-1 border-t my-2"></div>
            <span class="text-white font-extralight"
              >ระบบบริหารจัดการที่จอดรถอัจฉริยะ</span
            >
          </div>
      </div>
    </div>
      <div class="p-8">
        <div class="justify-center items-center text-center flex mx-auto">
          <img class="h-16 sm:h-20" src="../assets/images/logo.svg" />
          <div class="text-3xl sm:text-5xl">
            <span class="font-light"
              >Planet<span class="font-normal text-lime-500">EV</span></span
            >
          </div>
        </div>
        <form>
          <div class="relative mb-4 mt-20" data-te-input-wrapper-init>
            <input
              style="border: 1px solid #1ab6c1"
              class="w-full sm:w-64 md:w-80 lg:w-90 py-2 px-4 rounded-md focus:outline-none focus:ring-2 focus:ring-cyan-300 text-cyan-600"
              placeholder="Username"
            />
          </div>
          <div class="relative mb-4" data-te-input-wrapper-init>
            <input
              style="border: 1px solid #1ab6c1"
              class="w-full sm:w-64 md:w-80 lg:w-90 py-2 px-4 rounded-md focus:outline-none focus:ring-2 focus:ring-cyan-300 text-cyan-600"
              placeholder="Password"
            />
          </div>
          <div class="mb-12 pt-4 pb-1 text-center">
            <button
              class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full rounded px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
              type="button"
            >
              เข้าสู่ระบบ
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>


<script>
export default {
  name: "NuxtTutorial",
};
</script>
