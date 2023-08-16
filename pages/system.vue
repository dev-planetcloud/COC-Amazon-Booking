<template>
  <div class="system-content justify-center min-h-screen bg-white">
    <div class="bg-white h-full sm:overflow-hidden">
      <Header />
    </div>
    <div class="mt-14 p-4 pb-1">
      <div class="pl-6 pr-6 sm:pl-[20%] sm:pr-[20%]">
        <div class="flex justify-center">
          <div class="w-full flex justify-around">
            <div class="text-center">
              <button
                class="border-[1px] border-[#2AADCE] mb-3 inline-block w-[12vh] sm:w-[30vh] rounded px-4 sm:px-20 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-[#2AADCE]  transition duration-150 ease-in-out  focus:outline-none focus:ring-0 "
                type="submit"
                @click="activeDiv = 'Home'"
                :class="{'bg-[#2AADCE] text-white ': activeDiv === 'Home'}"
              >
                <span class="text-xs sm:text-base">จอง</span>
              </button>
            </div>
            <div class="text-center">
              <button
                class="border-[1px] border-[#2AADCE] mb-3 inline-block w-[12vh] sm:w-[30vh] rounded px-4 sm:px-20 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-[#2AADCE]  transition duration-150 ease-in-out focus:outline-none focus:ring-0 "
                type="button"
                @click="activeDiv = 'History'"
                :class="{'bg-[#2AADCE] text-white ': activeDiv === 'History'}"
                
              >
                <span class="text-xs sm:text-base">ประวัติการจอง</span>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
    <div class="pl-10 pr-10">
      <div v-if="activeDiv === 'Home'">
        <BookingHome />
      </div>
      <div v-if="activeDiv === 'History'">
        <BookingHistory />
      </div>
    </div>
  </div>
</template>



<script>
export default {
  data() {
    return {
      activeDiv: "Home",
    };
  },
  mounted() {},
  methods: {},
};
</script>



