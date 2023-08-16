<template>
  <div class="flex-1 sm:flex">
    <div class="w-full sm:w-full lg:flex-1">
      <div class="p-4" style="border-radius: 30px; border: 1px solid #26aec7">
        <span class="text-[#8C8B9D]">จำนวนรถเข้าใช้บริการ ณ ปัจจุบัน</span>
        <div class="justify-around flex p-4 pb-2 text-center">
          <div class="">
            <span style="color: #26aec7">ช่องจอดว่าง</span>
            <div class="text-[#66647C]">
              {{ access.blank }} <span style="color: #26aec7">ช่อง</span>
            </div>
          </div>
          <div>
            <span style="color: #26aec7">ช่องจอดเต็ม</span>
            <div class="text-[#66647C]">
              {{ access.full }} <span style="color: #26aec7">ช่อง</span>
            </div>
          </div>
          <div>
            <span style="color: #26aec7">จองช่องจอด</span>
            <div class="text-[#66647C]">
              {{ access.book }} <span style="color: #26aec7">ช่อง</span>
            </div>
          </div>
        </div>
      </div>

      <div
        class="mt-4 p-4 h-[28rem] sm:h-[41rem]"
        style="border-radius: 30px; border: 1px solid #26aec7"
      >
        <div class="text-center">
          <fa :icon="['fas', 'gear']" style="color: #8c8b9d" />
          <span class="text-[#8C8B9D] text-sm lg:text-base sm:text-sm"
            >คลิ๊กที่ช่องจอดรถเพื่อตั้งค่าช่องจอด</span
          >
        </div>
        <div class="px-2 h-[95%] sm:h-[95%]">
          <ParkingSelectPark />
        </div>
      </div>
    </div>

    <div class="w-full sm:w-1/2 sm:hidden lg:hidden xl:block">
      <div class="pt-4 sm:pt-0 sm:ml-4 sm:h-full grid gap-4 sm:grid-cols-2">
        <div
          class="p-4 h-64 text-center shadow block sm:hidden md:hidden lg:hidden xl:block"
          style="border-radius: 30px; border: 1px solid #26aec7"
        >
          <p class="text-[#66647C]">การบริหารจัดการพื้นที่จอดรถ</p>

          <div
            class="h-4/5 w-full flex items-center justify-center text-center"
          >
            <div
              class="w-[160px] h-[160px] items-center justify-center relative"
            >
              <div class="chart-container">
                <canvas id="system-chart"></canvas>
              </div>

              <div
                class="absolute top-2/4 left-2/4 transform -translate-y-2/4 -translate-x-2/4"
              >
                <div class="text-6xl mt-1 text-[#66647C]">
                  {{ access.full + access.blank }}
                </div>
                <span class="text-[#66647C]">ช่อง</span>
              </div>
            </div>
          </div>
          <div class="text-center">
            <span class="text-[#26ADC9]">เปิด {{ access.full }} |</span>
            <span class="text-[#66647C]">ปิด {{ access.blank }}</span>
          </div>
        </div>

        <div
          class="p-4 h-64 text-center shadow block sm:hidden md:hidden lg:hidden xl:block"
          style="border-radius: 30px; border: 1px solid #26aec7"
        >
          <div class="flex justify-between ">
            <div></div>
            <span class="text-[#66647C]">รถเข้าใช้บริการประจำวัน</span>
            <img src="../../assets/images/ChevronLeft.svg" />
          </div>

          <div class="h-4/5 w-full items-center justify-center py-12">
            <span class="text-7xl" style="color: #2badcf">20</span>
            <span class="text-end text-[#66647C]">ครั้ง</span>
          </div>
          <div class="text-center">
            <span class="text-[#26ADC9]">ผ่านระบบ {{ access.full }} |</span>
            <span class="text-[#66647C]">ไม่ผ่านระบบ 10</span>
          </div>
        </div>

        <div
          class="p-4 h-64 text-center shadow block sm:hidden md:hidden lg:hidden xl:block"
          style="border-radius: 30px; border: 1px solid #26aec7"
        >
          <div class="flex justify-between">
            <div></div>
            <div class="flex justify-center">
              <img class="" src="../../assets/images/Taxi Mobile App.svg" />
              <span class="text-[#66647C]">การจองช่องจอดรถล่วงหน้า</span>
            </div>
            <img src="../../assets/images/ChevronLeft.svg" />
          </div>

          <p class="mountTH text-[#66647C]">เดือน</p>
          <div class="h-4/5 w-full items-center justify-center py-8">
            <span class="text-7xl text-[#2badcf]">20</span>
            <span class="text-end text-[#66647C]">ครั้ง</span>
          </div>
        </div>

        <div
          class="p-4 h-64 text-center shadow block sm:hidden md:hidden lg:hidden xl:block"
          style="border-radius: 30px; border: 1px solid #26aec7"
        >
          <div class="flex justify-between">
            <div></div>
            <div class="flex justify-center">
              <img class="" src="../../assets/images/Wall Mount Camera.svg" />
              <span class="text-[#66647C]">กล้องวงจรปิด(CCTV)</span>
            </div>
            <img src="../../assets/images/ChevronLeft.svg" />
          </div>

          <div
            class="h-3/4 w-full flex items-center justify-center text-center"
          >
            <div
              class="w-[160px] h-[175x] items-center justify-center relative"
            >
              <!-- <canvas id="cctv-chart"></canvas> -->
              <div class="chart-container">
                <canvas id="cctv-chart"></canvas>
              </div>
              <div
                class="absolute top-2/4 left-2/4 transform -translate-y-2/4 -translate-x-2/4"
              >
                <div class="text-6xl mt-1 text-[#66647C]">
                  {{ access.full + access.blank }}
                </div>
                <span class="text-[#66647C]">ตัว</span>
              </div>
            </div>
          </div>
          <div class="text-center">
            <span class="text-[#26ADC9]">ออนไลน์ {{ access.full }} |</span>
            <span class="text-[#66647C]">ออฟไลน์ {{ access.blank }}</span>
          </div>
        </div>

        <div
          class="p-4 h-64 text-center shadow block sm:hidden md:hidden lg:hidden xl:block"
          style="border-radius: 30px; border: 1px solid #26aec7"
        >
          <div class="flex justify-between">
            <div></div>
            <p class="text-[#66647C]">ตั้งค่าการแจ้งเตือน user</p>
            <img src="../../assets/images/ChevronLeft.svg" />
          </div>
          <div class="h-5/6 flex justify-center items-center">
            <img src="../../assets/images/Users Settings.svg" />
          </div>
        </div>

        <div
          class="p-4 h-64 text-center shadow block sm:hidden md:hidden lg:hidden xl:block"
          style="border-radius: 30px; border: 1px solid #26aec7"
        >
          <div class="flex justify-between">
            <div></div>
            <p class="text-[#66647C] ">
              QR Code สำหรับลูกค้า
            </p>
            <img
              class="cursor-pointer"
              src="../../assets/images/ChevronLeft.svg"
            />
          </div>
          <div class="h-5/6 flex justify-center items-center">
            <img src="../../assets/images/Qr Code.svg" />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Chart from "chart.js/auto";

let myChart;
// let myChartCCTV;
export default {
  data() {
    return {
      access: {
        full: 2,
        blank: 4,
        book: 5,
      },
      chart_data: [],
      myChartCCTV: null,
    };
  },
  mounted() {
    this.setDateTime();
    this.setChartManage();
    this.intervalId = setInterval(this.updateChartM, 500);

    this.setChartCCTV();
    this.intervalId = setInterval(this.updateChartCCTV, 500);
  },
  computed: {
    gradientpole() {
      const ctx = document.getElementById("system-chart").getContext("2d");
      const gradientpole = ctx.createLinearGradient(0, 0, 0, 350);
      gradientpole.addColorStop(0.1, "#28ADCB");
      gradientpole.addColorStop(0.4, "#07AE9C");

      return gradientpole;
    },

    gradientCCTV() {
      const ctxCCTV = document.getElementById(`cctv-chart`).getContext("2d");
      const gradientCCTV = ctxCCTV.createLinearGradient(0, 0, 0, 350);
      gradientCCTV.addColorStop(0.1, "#28ADCB");
      gradientCCTV.addColorStop(0.4, "#07AE9C");

      return gradientCCTV;
    },
  },
  methods: {
    setDateTime() {
      const timeTH = document.querySelector(".mountTH");

      function datetime() {
        var month_name_th = [
          "มกราคม",
          "กุมภาพันธ์",
          "มีนาคม",
          "เมษายน",
          "พฤษภาคม",
          "มิถุนายน",
          "กรกฎาคม",
          "สิงหาคม",
          "กันยายน",
          "ตุลาคม",
          "พฤศจิกายน",
          "ธันวาคม",
        ];

        var dt = new Date();
        var date = dt.getDate();
        var month_th = month_name_th[dt.getMonth()];
        var year_th = dt.getFullYear() + 543;

        // ชั่วโมง น้อยกว่า 0 จะเป็น : 0x:
        if (parseInt(dt.getHours()) < 10) {
          var mh = "0" + dt.getHours();
        } else {
          var mh = dt.getHours();
        }
        // นาที น้อยกว่า 0 จะเป็น : 0x:
        if (parseInt(dt.getMinutes()) < 10) {
          var mm = "0" + dt.getMinutes();
        } else {
          var mm = dt.getMinutes();
        }
        // วินา น้อยกว่า 0 จะเป็น : 0x:
        if (parseInt(dt.getSeconds()) < 10) {
          var ms = "0" + dt.getSeconds();
        } else {
          var ms = dt.getSeconds();
        }

        var time = `${mh}:${mm}:${ms}`;

        // var datetime_th = date + " " + month_th + " " + year_th + " " + time;
        var datetime_th = "เดือน" + month_th;
        return datetime_th;
      }

      setInterval(() => {
        timeTH.textContent = datetime();
      }, 200);
    },
    // Chart Manage
    setChartManage() {
      const ctx = document.getElementById(`system-chart`);
      const ctxCCTV = document.getElementById(`cctv-chart`);

      const options = {
        layout: {
          padding: {
            left: -10,
          },
        },
        plugins: {
          tooltip: {
            enabled: false,
          },
          legend: {
            display: false,
          },
        },
        scales: {
          x: {
            ticks: {
              display: false,
            },
            grid: {
              display: false,
              drawBorder: false,
            },
          },
          y: {
            ticks: {
              display: false,
            },
            grid: {
              display: false,
              drawBorder: false,
            },
          },
        },
      };

      const data = {
        labels: ["เปิดอยู่", "ปิดอยู่"],
        datasets: [
          {
            data: [0, 0],
            backgroundColor: [this.gradientpole, "#d1d5db"],
            // borderColor: [gradientpole, "#d1d5db"],
            // borderColor: "transparent",
            // borderRadius: [100, 0],
            borderWidth: 0,
            cutout: "75%",
          },
        ],
      };

      const config = {
        type: "doughnut",
        data,
        options,
      };

      Chart.defaults.font.family = "Kanit";
      Chart.defaults.font.size = 12;
      Chart.defaults.color = "white";
      Chart.defaults.font.weight = 300;
      myChart = new Chart(ctx, config);
      // myChartCCTV = new Chart(ctxCCTV, config)
    },

    updateChartM() {
      myChart.data.datasets[0].data = [30, 10];
      myChart.update();
    },

    // Chart CCTV
    setChartCCTV() {
      const ctxCCTV = document.getElementById(`cctv-chart`);

      const options = {
        layout: {
          padding: {
            left: -10,
          },
        },
        plugins: {
          tooltip: {
            enabled: false,
          },
          legend: {
            display: false,
          },
        },
        scales: {
          x: {
            ticks: {
              display: false,
            },
            grid: {
              display: false,
              drawBorder: false,
            },
          },
          y: {
            ticks: {
              display: false,
            },
            grid: {
              display: false,
              drawBorder: false,
            },
          },
        },
        responsive: true,
      };

      const data = {
        labels: ["เปิดอยู่", "ปิดอยู่"],
        datasets: [
          {
            data: [0, 0],
            backgroundColor: [this.gradientCCTV, "#d1d5db"],
            // borderColor: [gradientpole, "#d1d5db"],
            // borderColor: "transparent",
            // borderRadius: [100, 0],
            borderWidth: 0,
            cutout: "75%",
          },
        ],
      };

      const config = {
        type: "doughnut",
        data,
        options,
      };

      Chart.defaults.font.family = "Kanit";
      Chart.defaults.font.size = 12;
      Chart.defaults.color = "white";
      Chart.defaults.font.weight = 300;
      this.myChartCCTV = new Chart(ctxCCTV, config);
    },
    updateChartCCTV() {
      this.myChartCCTV.data.datasets[0].data = [30, 10];
      this.myChartCCTV.update();
    },
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