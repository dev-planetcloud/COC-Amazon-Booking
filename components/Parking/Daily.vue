<template>
  <div class="h-full p-0 pt-0 sm:p-4">
    <div
      class="text-center sm:text-left items-center justify-center text-[#144779]"
    >
      รายการเข้าใช้บริการประจำวัน
      <div
        class="mt-3 sm:text-left sm:justify-between sm:w-full md:w-full lg:w-4/5 sm:flex text-center items-center justify-center"
      >
        <div class="relative text-lg z-20">
          <button
            class="flex items-center justify-between px-3 py-1 bg-white w-full sm:w-[14vh] md:w-[16vh] lg:w-[16vh] xl:w-[18vh] border border-[#2BADCF] rounded-[30px]"
            @click="isOptionsExpanded = !isOptionsExpanded"
            @blur="isOptionsExpanded = false"
          >
            <div></div>
            <span style="color: #8c8b9d; font-size: 16px">
              {{ selectedOption }}</span
            >
            <svg
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              class="h-4 w-4 transform transition-transform duration-200 ease-in-out text-[#8C8B9D]"
              :class="isOptionsExpanded ? 'rotate-180' : 'rotate-0'"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M19 9l-7 7-7-7"
              />
            </svg>
          </button>
          <transition
            enter-active-class="transform transition duration-500 ease-custom"
            enter-class="-translate-y-1/2 scale-y-0 opacity-0"
            enter-to-class="translate-y-0 scale-y-100 opacity-100"
            leave-active-class="transform transition duration-300 ease-custom"
            leave-class="translate-y-0 scale-y-100 opacity-100"
            leave-to-class="-translate-y-1/2 scale-y-0 opacity-0"
          >
            <ul
              v-show="isOptionsExpanded"
              class="absolute left-0 right-0 mb-4 bg-white divide-y rounded-lg shadow-lg overflow-hidden"
            >
              <li
                v-for="(option, index) in options"
                :key="index"
                class="px-3 py-2 transition-colors duration-300 hover:bg-gray-200 text-[#26ADC9] text-center"
                @mousedown.prevent="setOption(option)"
              >
                {{ option }}
              </li>
            </ul>
          </transition>
        </div>

        <div class="relative text-lg z-10 mt-5 sm:mt-0">
          <button
            class="flex items-center justify-between px-3 py-1 bg-white w-full sm:w-[14vh] md:w-[16vh] lg:w-[16vh] xl:w-[18vh] border border-[#2BADCF] rounded-[30px]"
            @click="isOptionsExpandedCar = !isOptionsExpandedCar"
            @blur="isOptionsExpandedCar = false"
          >
            <div></div>
            <span style="color: #8c8b9d; font-size: 16px">
              {{ selectedOptionCar }}</span
            >
            <svg
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              class="h-4 w-4 transform transition-transform duration-200 ease-in-out text-[#8C8B9D]"
              :class="isOptionsExpandedCar ? 'rotate-180' : 'rotate-0'"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M19 9l-7 7-7-7"
              />
            </svg>
          </button>
          <transition
            enter-active-class="transform transition duration-500 ease-custom"
            enter-class="-translate-y-1/2 scale-y-0 opacity-0"
            enter-to-class="translate-y-0 scale-y-100 opacity-100"
            leave-active-class="transform transition duration-300 ease-custom"
            leave-class="translate-y-0 scale-y-100 opacity-100"
            leave-to-class="-translate-y-1/2 scale-y-0 opacity-0"
          >
            <ul
              v-show="isOptionsExpandedCar"
              class="absolute left-0 right-0 mb-4 bg-white divide-y rounded-lg shadow-lg overflow-hidden"
            >
              <li
                v-for="(option, index) in optionsCar"
                :key="index"
                class="px-3 py-2 transition-colors duration-300 hover:bg-gray-200 text-[#26ADC9] text-center"
                @mousedown.prevent="setOptionCar(option)"
              >
                {{ option }}
              </li>
            </ul>
          </transition>
        </div>

        <div class="relative text-lg z-10 mt-5 sm:mt-0">
          <button
            class="flex items-center justify-between px-3 py-1 bg-white w-full sm:w-[14vh] md:w-[16vh] lg:w-[16vh] xl:w-[18vh] border border-[#2BADCF] rounded-[30px]"
            @click="isOptionsExpandedPass = !isOptionsExpandedPass"
            @blur="isOptionsExpandedPass = false"
          >
            <div></div>
            <span style="color: #8c8b9d; font-size: 16px">
              {{ selectedOptionPass }}</span
            >
            <svg
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              class="h-4 w-4 transform transition-transform duration-200 ease-in-out text-[#8C8B9D]"
              :class="isOptionsExpandedPass ? 'rotate-180' : 'rotate-0'"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M19 9l-7 7-7-7"
              />
            </svg>
          </button>
          <transition
            enter-active-class="transform transition duration-500 ease-custom"
            enter-class="-translate-y-1/2 scale-y-0 opacity-0"
            enter-to-class="translate-y-0 scale-y-100 opacity-100"
            leave-active-class="transform transition duration-300 ease-custom"
            leave-class="translate-y-0 scale-y-100 opacity-100"
            leave-to-class="-translate-y-1/2 scale-y-0 opacity-0"
          >
            <ul
              v-show="isOptionsExpandedPass"
              class="absolute left-0 right-0 mb-4 bg-white divide-y rounded-lg shadow-lg overflow-hidden"
            >
              <li
                v-for="(option, index) in optionsPass"
                :key="index"
                class="px-3 py-2 transition-colors duration-300 hover:bg-gray-200 text-[#26ADC9] text-center"
                @mousedown.prevent="setOptionPass(option)"
              >
                {{ option }}
              </li>
            </ul>
          </transition>
        </div>

        <div class="relative text-lg mt-5 sm:mt-0">
          <div
            class="flex items-center px-3 py-1 bg-white w-full sm:w-[14vh] md:w-[16vh] lg:w-[16vh] xl:w-[18vh] border border-[#2BADCF] rounded-[30px]"
          >
            <input
              type="text"
              placeholder="ค้นหา"
              class="p-0 w-full text-[#8C8B9D] focus:outline-none text-center"
              v-model="searchText"
            />
            <svg
              aria-hidden="true"
              class="w-5 h-5 text-[#2BADCF] dark:text-gray-400"
              fill="none"
              stroke="currentColor"
              viewBox="0 0 24 24"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z"
              ></path>
            </svg>
          </div>
        </div>
      </div>
    </div>
    <div
      class="mt-4 justify-between flex text-[#8C8B9D] p-2 md:px-4 text-center"
    >
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">วันที่ทำรายการ</span>
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">ทะเบียน</span>
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">ประเภทรถ</span>
      <span class="w-3/12 hidden lg:block">เวลาจองใช้บริการ</span>
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">ช่องจอด</span>
      <span class="w-3/12 hidden lg:block text-xs lg:text-base sm:text-sm"
        >ช่องทาง</span
      >
      <span class="w-3/12 hidden lg:block">ชื่อ-นามสกุล</span>
      <span class="w-3/12 hidden xl:block">เบอร์โทรศัพท์</span>
    </div>

    <div class="relative overflow-x-auto h-[65vh] w-full">
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
        <!-- Column -->
        <div
          class="my-1 px-1 w-full lg:my-2 lg:px-4"
          v-for="(booking, index) in filteredDatil_day"
          :key="index"
        >
          <article class="overflow-hidden rounded-lg border border-[#2BADCF]">
            <div
              class="flex items-center justify-between leading-tight p-2 md:p-4 text-center"
            >
              <span class="w-3/12 text-xs sm:text-sm lg:text-base">{{
                booking.date_now
              }}</span>
              <div
                class="w-3/12 bg-[#F7F9FB] border border-[#E5E0E9] p-1 rounded-[5px] text-center lg:p-3"
              >
                <div class="text-xs lg:text-base sm:text-sm mb-1">
                  {{ booking.license_plate.num }}
                </div>
                <div
                  class="text-xs lg:text-base sm:text-sm whitespace-nowrap overflow-hidden text-overflow-ellipsis"
                >
                  {{ booking.license_plate.text }}
                </div>
              </div>
              <span class="w-3/12 text-xs lg:text-base sm:text-sm">{{
                booking.type
              }}</span>
              <span class="w-3/12 hidden lg:block">{{
                booking.service_now
              }}</span>
              <span
                class="w-3/12 hidden lg:block text-xs lg:text-base sm:text-sm"
                >{{ booking.parking_space }}</span
              >
              <span class="w-3/12 text-xs lg:text-base sm:text-sm">{{
                booking.funnel
              }}</span>
              <span class="w-3/12 hidden lg:block">{{ booking.name }}</span>
              <span class="w-3/12 hidden xl:block">{{ booking.phone }}</span>
            </div>
          </article>
        </div>
        <!-- END Column -->
      </div>
    </div>
  </div>
</template>


<script>
export default {
  data() {
    return {
      isOptionsExpanded: false,
      selectedOption: "วันนี้",
      options: ["วันนี้", "สัปดาห์นี้", "เดือนนี้", "ปีนี้", "กำหนดเอง"],

      isOptionsExpandedCar: false,
      selectedOptionCar: "รถทุกประเภท",
      optionsCar: ["EV", "อื่นๆ"],

      isOptionsExpandedPass: false,
      selectedOptionPass: "ทุกช่องทาง",
      optionsPass: ["จองผ่านระบบ", "ไม่ผ่านระบบ"],

      searchText: "",

      datil_day: [
        {
          id: 1,
          date_now: "20/03/2566 09:00",
          license_plate: { num: 39990, text: "กรุงเทพมหานคร" },
          type: "EV",
          service_now: "20/03/2566 10:00",
          parking_space: "P03",
          funnel: "จองผ่านระบบ",
          name: "Payupat Sutaom",
          phone: "088-2339019",
        },
        {
          id: 2,
          date_now: "20/03/2566 09:00",
          license_plate: { num: 1912, text: "กรุงเทพมหานคร" },
          type: "General",
          service_now: "20/03/2566 10:00",
          parking_space: "P02",
          funnel: "ไม่ผ่านระบบ",
          name: "pawit",
          phone: "02-020-0999",
        },
      ],
    };
  },
  computed: {
    filteredDatil_day() {
      let filtered = this.datil_day.filter(
        (booking) =>
          booking.date_now
            .toLowerCase()
            .includes(this.searchText.toLowerCase()) ||
          booking.license_plate.text
            .toLowerCase()
            .includes(this.searchText.toLowerCase()) ||
          booking.type.toLowerCase().includes(this.searchText.toLowerCase()) ||
          booking.service_now
            .toLowerCase()
            .includes(this.searchText.toLowerCase()) ||
          booking.parking_space
            .toLowerCase()
            .includes(this.searchText.toLowerCase()) ||
          booking.funnel
            .toLowerCase()
            .includes(this.searchText.toLowerCase()) ||
          booking.name.toLowerCase().includes(this.searchText.toLowerCase()) ||
          booking.phone.toLowerCase().includes(this.searchText.toLowerCase())
      );

      if (this.selectedOptionCar === "EV") {
        filtered = filtered.filter((booking) => booking.type === "EV");
      } else if (this.selectedOptionCar === "อื่นๆ") {
        filtered = filtered.filter((booking) => booking.type !== "EV");
      }

      if (this.selectedOptionPass === "จองผ่านระบบ") {
        filtered = filtered.filter(
          (booking) => booking.funnel === "จองผ่านระบบ"
        );
      } else if (this.selectedOptionPass === "ไม่ผ่านระบบ") {
        filtered = filtered.filter(
          (booking) => booking.funnel === "ไม่ผ่านระบบ"
        );
      }

      return filtered;
    },
  },
  methods: {
    setOption(option) {
      this.selectedOption = option;
      this.isOptionsExpanded = false;
    },

    setOptionCar(option) {
      this.selectedOptionCar = option;
      this.isOptionsExpandedCar = false;
    },

    setOptionPass(option) {
      this.selectedOptionPass = option;
      this.isOptionsExpandedPass = false;
    },
  },
};
</script>

<style>
.ease-custom {
  transition-timing-function: cubic-bezier(0.61, -0.53, 0.43, 1.43);
}
</style>