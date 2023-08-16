<template>
  <div class="flex-1 sm:flex">
    <div class="sm:pl-[10%] sm:pr-[10%] w-full sm:w-full lg:flex-1">
      <div class="sm:px-20">
        <span class="text-[#152C5B]">วันที่ต้องการจอง</span>
        <div>
          <input
            type="date"
            class="px-3 py-1 text-black rounded-md w-full sm:w-[230px] focus:outline-none border border-[#26aec7] text-center"
            @change="selectedDate = $event.target.value"
            v-model="selectedDate"
            :min="new Date().toISOString().split('T')[0]"
          />

          <!-- <span v-else class="font-semibold text-xl">ออกรายงาน</span> -->
        </div>
        <span v-if="selectedDate === ''" class="text-red-500 text-xs">กรุณาเลือกวันที่</span>
      </div>

      <div class="sm:px-20 mt-2 h-[28rem] sm:h-[35rem]">
        <div class="text-left">
          <span class="text-[#152C5B] text-sm lg:text-base sm:text-sm"
            >เลือกช่องที่ต้องการ</span
          >
        </div>
        <div class="h-[95%] sm:h-[95%]">
          <BookingSelectPark />
        </div>
      </div>

      <div class="sm:px-20 mt-2">
        <span>เวลาที่คุณสามารถจองได้</span>

        <span class="text-[#152C5B]">วันที่ต้องการจอง</span>
        <div>
          <input
            type="time"
            class="px-3 py-1 text-black rounded-md w-full sm:w-[230px] focus:outline-none border border-[#26aec7] text-center"
            @change="selectedTime = $event.target.value"
            v-model="selectedTime"
            placeholder="--Select Time--"
            :min="new Date().toISOString().split('T')[0]"
          />
        </div>
       <span v-if="selectedTime === ''" class="text-red-500 text-xs">กรุณาเลือกเวลา</span>

        <div class="mb-1 pt-4 pb-1">
          <button
            class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full sm:w-[230px] rounded px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
            type="submit"
            @click="handle()"
          >
            <span class="text-xl">ยืนยันการจอง</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Swal from 'sweetalert2/dist/sweetalert2.js'
import 'sweetalert2/dist/sweetalert2.min.css';

export default {
  data() {
    return {
      selectedDate: "",
      selectedTime: ""
      
    };
  },
  mounted() {},
  computed: {},
  methods: {
    handle() {
      if (this.selectedDate === "" || this.selectedTime === "") {
        Swal.fire({
          title: 'Error!',
          text: 'ทำการจองล้มเหลว โปรดทำการจองใหม่อีกครั้ง',
          icon: 'error',
          confirmButtonText: 'ปิด'
        })
        console.log(this.selectedDate);
      } else {
        // alert("Success");
        Swal.fire({
          icon: 'success',
          title: 'ทำการจองสำเร็จ',
          showConfirmButton: false,
          timer: 2000
        })
        // this.$router.push('../system');
      }
    }
  },
};
</script>

<style>
.chart-container {
  position: relative;
  width: 100%;
  height: 0;
  padding-bottom: 100%; /* 1:1 aspect ratio */
}
.chart-container canvas {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>