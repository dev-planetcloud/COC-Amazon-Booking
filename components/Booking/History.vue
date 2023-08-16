<template>
  <div class="h-full p-0 pt-0 sm:px-20">
    <div
      class="text-center sm:text-left items-center justify-center text-[#144779]"
    >
      <span>รายการจองคิวล่วงหน้า ({{ bookings.length }})</span>

    </div>

    <div
      class="mt-4 justify-between flex text-[#8C8B9D] p-2 md:px-4 text-center"
    >
      <span class="w-3/12 hidden lg:block text-xs lg:text-base sm:text-sm">วันที่ทำรายการ</span>
      <span class="w-3/12 hidden lg:block text-xs lg:text-base sm:text-sm">ทะเบียน</span>
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">วันที่ใช้บริการ</span>
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">ช่องจอด</span>
      <span class="w-3/12 text-xs lg:text-base sm:text-sm">สถานะ</span>
    </div>

    <div class="relative  h-[65vh] w-full">
      <div class="flex flex-wrap -mx-1 lg:-mx-4">
        <!-- Column -->
        <div
          class="my-1 px-1 w-full lg:my-2 lg:px-4"
          v-for="(booking, index) in filteredBookings"
          :key="index"
        >
          <article class="overflow-hidden rounded-lg border border-[#2BADCF]">
            <div
              class="flex items-center justify-between leading-tight p-2 md:p-4 text-center"
            >
              <span class="w-3/12 hidden lg:block text-xs sm:text-sm lg:text-base">{{
                booking.date_now
              }}</span>
              <div
                class="w-3/12 hidden lg:block bg-[#F7F9FB] border border-[#E5E0E9] p-1 rounded-[5px] text-center lg:p-3"
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
                booking.service_now
              }}</span>
              <span class="w-3/12 text-xs lg:text-base sm:text-sm">{{
                booking.parking_space
              }}</span>
              <span class="w-3/12  text-xs lg:text-base sm:text-sm">{{
                booking.status
              }}</span>
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
      selectedOption: "เลือกวัน",
      options: ["วันนี้", "สัปดาห์นี้", "เดือนนี้", "ปีนี้", "กำหนดเอง"],

      isOptionsExpandedCar: false,
      selectedOptionCar: "รถทุกประเภท",
      optionsCar: ["EV", "อื่นๆ"],

      searchText: "",

      bookings: [
        {
          id: 1,
          date_now: "20/03/2566 09:00",
          license_plate: { num: "39990", text: "กรุงเทพมหานคร" },
          type: "EV",
          service_now: "20/03/2566 10:00",
          parking_space: "P03",
          name: "Payupat Sutaom",
          phone: "088-2339019",
          status:'จอง'
        },
        {
          id: 2,
          date_now: "25/03/2566 09:00",
          license_plate: { num: "1912", text: "เชียงราย" },
          type: "General",
          service_now: "20/03/2566 12:00",
          parking_space: "P02",
          name: "pawit",
          phone: "02-020-0999",
          status:'เสร็จสิ้น'
        },
      ],
    };
  },
  computed: {
    filteredBookings() {
      let filtered = this.bookings.filter(
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
          booking.name.toLowerCase().includes(this.searchText.toLowerCase()) ||
          booking.phone.toLowerCase().includes(this.searchText.toLowerCase())
      );

      if (this.selectedOptionCar === "EV") {
        filtered = filtered.filter((booking) => booking.type === "EV");
      } else if (this.selectedOptionCar === "อื่นๆ") {
        filtered = filtered.filter((booking) => booking.type !== "EV");
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
  },
};
</script>

<style>
.ease-custom {
  transition-timing-function: cubic-bezier(0.61, -0.53, 0.43, 1.43);
}
</style>