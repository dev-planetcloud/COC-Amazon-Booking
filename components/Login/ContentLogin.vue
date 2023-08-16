<!-- Please remove this file from your project -->
<template>
  <div
    class="max-w-md mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-3xl"
  >
    <div class="md:flex">
      <div class="md:shrink-0 relative">
        <img
          class="h-80 w-full object-cover md:h-full md:w-96"
          src="../../assets/images/imglogin.svg"
        />
        <div
          class="absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 text-center"
        >
          <div class="text-left">
            <span class="text-white text-5xl sm:text-6xl">Welcome</span><br />
            <span class="text-white text-xl font-extralight"
              >To Parking Dashboard</span
            ><br />
            <div class="bg-white col-span-1 border-t my-2"></div>
            <span class="text-white font-extralight text-xs sm:text-base"
              >ระบบบริหารจัดการที่จอดรถอัจฉริยะ</span
            >
          </div>
        </div>
      </div>
      <div class="rounded-md">
        <div class="p-8">
          <div class="justify-center items-center text-center flex mx-auto">
            <img class="h-16 sm:h-20" src="../../assets/images/logo.svg" />
            <div class="text-3xl sm:text-5xl">
              <span class="font-light"
                >Planet<span class="font-normal text-lime-500">EV</span></span
              >
            </div>
          </div>
          <form @submit.prevent="handleSubmit">
            <div
              class="relative mb-4 mt-10 sm:mt-12"
              data-te-input-wrapper-init
            >
              <label class="text-[#A3BEC0]">กรอกทะเบียนรถของคุณ</label>
              <input
                id="vehicle_regis"
                v-model="vehicle_regis"
                style="border: 1px solid #1ab6c1"
                class="w-full md:w-80 lg:w-90 py-2 px-4 rounded-md bg-gray-50 focus:bg-white focus:outline-none focus:ring-2 focus:ring-cyan-300 text-cyan-600"
              />
            </div>
            <div class="relative mb-1" data-te-input-wrapper-init>
              <label class="text-[#A3BEC0]">จังหวัดของทะเบียนรถคุณ</label>
              <!-- <input
                id="province"
                v-model="province"
                @keyup="filterProvinces"
                style="border: 1px solid #1ab6c1"
                class="w-full md:w-80 lg:w-90 py-2 px-4 rounded-md bg-gray-50 focus:outline-none focus:ring-2 focus:ring-cyan-300 text-cyan-600"
              /> -->

              <select
                id="province"
                style="border: 1px solid #1ab6c1"
                class="w-full md:w-80 lg:w-90 py-2 px-4 rounded-md bg-gray-50 focus:outline-none focus:ring-2 focus:ring-cyan-300 text-cyan-600"
                v-model="selectedProvince"
              >
                <option value="">-- เลือกจังหวัด --</option>
                <option v-for="province in provincesAll" :value="province" :key="province.id">
                  {{ province.provinceNameTh }}
                </option>
              </select>
              

              <!-- <ul
                v-if="filteredProvinces.length"
                class="absolute top-full left-0 right-0 z-10 bg-white rounded-md shadow-md overflow-hidden"
              >
                <li
                  v-for="(province, index) in filteredProvinces"
                  :key="index"
                  class="px-3 py-2 cursor-pointer hover:bg-gray-100"
                  @click="provinceSelected(province)"
                >
                  {{ province }}
                </li>
              </ul> -->
            </div>


            <div class="mb-1 pt-4 pb-1 text-center">
              <button
                class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full rounded px-6 pt-2.5 pb-2 text-xs font-medium uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
                type="submit"
              >
                <span class="text-xl">เข้าสู่ระบบ</span>
              </button>
            </div>
            <div class="pb-1 text-center">
              <span
                class="text-xl underline text-[#138BBD] cursor-pointer"
                @click="policy"
                >ลงทะเบียน</span
              >
            </div>
          </form>

          <div
            :class="{ hidden: !showAlert }"
            class="bg-gray-200 bg-opacity-75 absolute inset-0 flex items-center justify-center"
          >
            <div
              class="bg-white w-[30vh] sm:w-[35vh] md:w-80 lg:w-90 h-[40%] rounded-[30px]"
            >
              <div class="p-4">
                <div class="flex items-center justify-center">
                  <img src="../../assets/images/icon plate.svg" />
                </div>
                <div class="text-center font-light mt-2">
                  <span class="text-[#1AB6C1] text-base"
                    >ไม่พบข้อมูลทะเบียนรถของคุณ</span
                  ><br />
                  <span class="text-[#B0B0B0] text-sm"
                    >กรุณาลงทะเบียนเพื่อใช้บริการ</span
                  >
                  <div class="pt-2 text-center">
                    <button
                      class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full rounded px-6 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
                      type="submit"
                      @click="policy"
                    >
                      <span class="text-base">ลงทะเบียน</span>
                    </button>
                  </div>
                  <div class="text-center">
                    <button
                      class="border-[1px] border-[#2AADCE] mb-3 inline-block w-full rounded px-6 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-[#2AADCE] shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
                      type="button"
                      @click="showAlert = false"
                    >
                      <span class="text-base">ยกเลิก</span>
                    </button>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>


<script>


export default {
  name: "NuxtTutorial",
  data() {
    return {
      selectedProvince: '',
      provincesAll: [
        {
          id: 1,
          provinceCode: 10,
          provinceNameEn: "Bangkok",
          provinceNameTh: "กรุงเทพมหานคร",
        },
        {
          id: 2,
          provinceCode: 11,
          provinceNameEn: "Samut Prakan",
          provinceNameTh: "สมุทรปราการ",
        },
        {
          id: 3,
          provinceCode: 12,
          provinceNameEn: "Nonthaburi",
          provinceNameTh: "นนทบุรี",
        },
        {
          id: 4,
          provinceCode: 13,
          provinceNameEn: "Pathum Thani",
          provinceNameTh: "ปทุมธานี",
        },
        {
          id: 5,
          provinceCode: 14,
          provinceNameEn: "Phra Nakhon Si Ayutthaya",
          provinceNameTh: "พระนครศรีอยุธยา",
        },
        {
          id: 6,
          provinceCode: 15,
          provinceNameEn: "Ang Thong",
          provinceNameTh: "อ่างทอง",
        },
        {
          id: 7,
          provinceCode: 16,
          provinceNameEn: "Loburi",
          provinceNameTh: "ลพบุรี",
        },
        {
          id: 8,
          provinceCode: 17,
          provinceNameEn: "Sing Buri",
          provinceNameTh: "สิงห์บุรี",
        },
        {
          id: 9,
          provinceCode: 18,
          provinceNameEn: "Chai Nat",
          provinceNameTh: "ชัยนาท",
        },
        {
          id: 10,
          provinceCode: 19,
          provinceNameEn: "Saraburi",
          provinceNameTh: "สระบุรี",
        },
        {
          id: 11,
          provinceCode: 20,
          provinceNameEn: "Chon Buri",
          provinceNameTh: "ชลบุรี",
        },
        {
          id: 12,
          provinceCode: 21,
          provinceNameEn: "Rayong",
          provinceNameTh: "ระยอง",
        },
        {
          id: 13,
          provinceCode: 22,
          provinceNameEn: "Chanthaburi",
          provinceNameTh: "จันทบุรี",
        },
        {
          id: 14,
          provinceCode: 23,
          provinceNameEn: "Trat",
          provinceNameTh: "ตราด",
        },
        {
          id: 15,
          provinceCode: 24,
          provinceNameEn: "Chachoengsao",
          provinceNameTh: "ฉะเชิงเทรา",
        },
        {
          id: 16,
          provinceCode: 25,
          provinceNameEn: "Prachin Buri",
          provinceNameTh: "ปราจีนบุรี",
        },
        {
          id: 17,
          provinceCode: 26,
          provinceNameEn: "Nakhon Nayok",
          provinceNameTh: "นครนายก",
        },
        {
          id: 18,
          provinceCode: 27,
          provinceNameEn: "Sa Kaeo",
          provinceNameTh: "สระแก้ว",
        },
        {
          id: 19,
          provinceCode: 30,
          provinceNameEn: "Nakhon Ratchasima",
          provinceNameTh: "นครราชสีมา",
        },
        {
          id: 20,
          provinceCode: 31,
          provinceNameEn: "Buri Ram",
          provinceNameTh: "บุรีรัมย์",
        },
        {
          id: 21,
          provinceCode: 32,
          provinceNameEn: "Surin",
          provinceNameTh: "สุรินทร์",
        },
        {
          id: 22,
          provinceCode: 33,
          provinceNameEn: "Si Sa Ket",
          provinceNameTh: "ศรีสะเกษ",
        },
        {
          id: 23,
          provinceCode: 34,
          provinceNameEn: "Ubon Ratchathani",
          provinceNameTh: "อุบลราชธานี",
        },
        {
          id: 24,
          provinceCode: 35,
          provinceNameEn: "Yasothon",
          provinceNameTh: "ยโสธร",
        },
        {
          id: 25,
          provinceCode: 36,
          provinceNameEn: "Chaiyaphum",
          provinceNameTh: "ชัยภูมิ",
        },
        {
          id: 26,
          provinceCode: 37,
          provinceNameEn: "Amnat Charoen",
          provinceNameTh: "อำนาจเจริญ",
        },
        {
          id: 27,
          provinceCode: 38,
          provinceNameEn: "Bueng Kan",
          provinceNameTh: "บึงกาฬ",
        },
        {
          id: 28,
          provinceCode: 39,
          provinceNameEn: "Nong Bua Lam Phu",
          provinceNameTh: "หนองบัวลำภู",
        },
        {
          id: 29,
          provinceCode: 40,
          provinceNameEn: "Khon Kaen",
          provinceNameTh: "ขอนแก่น",
        },
        {
          id: 30,
          provinceCode: 41,
          provinceNameEn: "Udon Thani",
          provinceNameTh: "อุดรธานี",
        },
        {
          id: 31,
          provinceCode: 42,
          provinceNameEn: "Loei",
          provinceNameTh: "เลย",
        },
        {
          id: 32,
          provinceCode: 43,
          provinceNameEn: "Nong Khai",
          provinceNameTh: "หนองคาย",
        },
        {
          id: 33,
          provinceCode: 44,
          provinceNameEn: "Maha Sarakham",
          provinceNameTh: "มหาสารคาม",
        },
        {
          id: 34,
          provinceCode: 45,
          provinceNameEn: "Roi Et",
          provinceNameTh: "ร้อยเอ็ด",
        },
        {
          id: 35,
          provinceCode: 46,
          provinceNameEn: "Kalasin",
          provinceNameTh: "กาฬสินธุ์",
        },
        {
          id: 36,
          provinceCode: 47,
          provinceNameEn: "Sakon Nakhon",
          provinceNameTh: "สกลนคร",
        },
        {
          id: 37,
          provinceCode: 48,
          provinceNameEn: "Nakhon Phanom",
          provinceNameTh: "นครพนม",
        },
        {
          id: 38,
          provinceCode: 49,
          provinceNameEn: "Mukdahan",
          provinceNameTh: "มุกดาหาร",
        },
        {
          id: 39,
          provinceCode: 50,
          provinceNameEn: "Chiang Mai",
          provinceNameTh: "เชียงใหม่",
        },
        {
          id: 40,
          provinceCode: 51,
          provinceNameEn: "Lamphun",
          provinceNameTh: "ลำพูน",
        },
        {
          id: 41,
          provinceCode: 52,
          provinceNameEn: "Lampang",
          provinceNameTh: "ลำปาง",
        },
        {
          id: 42,
          provinceCode: 53,
          provinceNameEn: "Uttaradit",
          provinceNameTh: "อุตรดิตถ์",
        },
        {
          id: 43,
          provinceCode: 54,
          provinceNameEn: "Phrae",
          provinceNameTh: "แพร่",
        },
        {
          id: 44,
          provinceCode: 55,
          provinceNameEn: "Nan",
          provinceNameTh: "น่าน",
        },
        {
          id: 45,
          provinceCode: 56,
          provinceNameEn: "Phayao",
          provinceNameTh: "พะเยา",
        },
        {
          id: 46,
          provinceCode: 57,
          provinceNameEn: "Chiang Rai",
          provinceNameTh: "เชียงราย",
        },
        {
          id: 47,
          provinceCode: 58,
          provinceNameEn: "Mae Hong Son",
          provinceNameTh: "แม่ฮ่องสอน",
        },
        {
          id: 48,
          provinceCode: 60,
          provinceNameEn: "Nakhon Sawan",
          provinceNameTh: "นครสวรรค์",
        },
        {
          id: 49,
          provinceCode: 61,
          provinceNameEn: "Uthai Thani",
          provinceNameTh: "อุทัยธานี",
        },
        {
          id: 50,
          provinceCode: 62,
          provinceNameEn: "Kamphaeng Phet",
          provinceNameTh: "กำแพงเพชร",
        },
        {
          id: 51,
          provinceCode: 63,
          provinceNameEn: "Tak",
          provinceNameTh: "ตาก",
        },
        {
          id: 52,
          provinceCode: 64,
          provinceNameEn: "Sukhothai",
          provinceNameTh: "สุโขทัย",
        },
        {
          id: 53,
          provinceCode: 65,
          provinceNameEn: "Phitsanulok",
          provinceNameTh: "พิษณุโลก",
        },
        {
          id: 54,
          provinceCode: 66,
          provinceNameEn: "Phichit",
          provinceNameTh: "พิจิตร",
        },
        {
          id: 55,
          provinceCode: 67,
          provinceNameEn: "Phetchabun",
          provinceNameTh: "เพชรบูรณ์",
        },
        {
          id: 56,
          provinceCode: 70,
          provinceNameEn: "Ratchaburi",
          provinceNameTh: "ราชบุรี",
        },
        {
          id: 57,
          provinceCode: 71,
          provinceNameEn: "Kanchanaburi",
          provinceNameTh: "กาญจนบุรี",
        },
        {
          id: 58,
          provinceCode: 72,
          provinceNameEn: "Suphan Buri",
          provinceNameTh: "สุพรรณบุรี",
        },
        {
          id: 59,
          provinceCode: 73,
          provinceNameEn: "Nakhon Pathom",
          provinceNameTh: "นครปฐม",
        },
        {
          id: 60,
          provinceCode: 74,
          provinceNameEn: "Samut Sakhon",
          provinceNameTh: "สมุทรสาคร",
        },
        {
          id: 61,
          provinceCode: 75,
          provinceNameEn: "Samut Songkhram",
          provinceNameTh: "สมุทรสงคราม",
        },
        {
          id: 62,
          provinceCode: 76,
          provinceNameEn: "Phetchaburi",
          provinceNameTh: "เพชรบุรี",
        },
        {
          id: 63,
          provinceCode: 77,
          provinceNameEn: "Prachuap Khiri Khan",
          provinceNameTh: "ประจวบคีรีขันธ์",
        },
        {
          id: 64,
          provinceCode: 80,
          provinceNameEn: "Nakhon Si Thammarat",
          provinceNameTh: "นครศรีธรรมราช",
        },
        {
          id: 65,
          provinceCode: 81,
          provinceNameEn: "Krabi",
          provinceNameTh: "กระบี่",
        },
        {
          id: 66,
          provinceCode: 82,
          provinceNameEn: "Phangnga",
          provinceNameTh: "พังงา",
        },
        {
          id: 67,
          provinceCode: 83,
          provinceNameEn: "Phuket",
          provinceNameTh: "ภูเก็ต",
        },
        {
          id: 68,
          provinceCode: 84,
          provinceNameEn: "Surat Thani",
          provinceNameTh: "สุราษฎร์ธานี",
        },
        {
          id: 69,
          provinceCode: 85,
          provinceNameEn: "Ranong",
          provinceNameTh: "ระนอง",
        },
        {
          id: 70,
          provinceCode: 86,
          provinceNameEn: "Chumphon",
          provinceNameTh: "ชุมพร",
        },
        {
          id: 71,
          provinceCode: 90,
          provinceNameEn: "Songkhla",
          provinceNameTh: "สงขลา",
        },
        {
          id: 72,
          provinceCode: 91,
          provinceNameEn: "Satun",
          provinceNameTh: "สตูล",
        },
        {
          id: 73,
          provinceCode: 92,
          provinceNameEn: "Trang",
          provinceNameTh: "ตรัง",
        },
        {
          id: 74,
          provinceCode: 93,
          provinceNameEn: "Phatthalung",
          provinceNameTh: "พัทลุง",
        },
        {
          id: 75,
          provinceCode: 94,
          provinceNameEn: "Pattani",
          provinceNameTh: "ปัตตานี",
        },
        {
          id: 76,
          provinceCode: 95,
          provinceNameEn: "Yala",
          provinceNameTh: "ยะลา",
        },
        {
          id: 77,
          provinceCode: 96,
          provinceNameEn: "Narathiwat",
          provinceNameTh: "นราธิวาส",
        },
      ],
      account: {
        user: "planetev",
        pass: "1234",
      },
      vehicle_regis: "",
      province: "",
      provinces: ["กรุงเทพ", "ระยอง", "ชลบุรี"],
      filteredProvinces: [],
      formData:[{
        id:1,
        plate:'123',
        province:'เชียงราย'
      },{
        id:2,
        plate:'191',
        province:'เชียงใหม่'
      },{
        id:3,
        plate:'123',
        province:'พะเยา'
      }],

      showAlert: false,
    };
  },
  mounted() {
    // document.addEventListener("click", (event) => {
    //   if (!this.$el.contains(event.target)) {
    //     this.filteredProvinces = [];
    //   }
    // });
  },
  methods: {
    handleSubmit() {
      console.log(this.selectedProvince);
      if (this.vehicle_regis === '' || this.selectedProvince === '') {
        this.showAlert = true;
      } else if(this.vehicle_regis == '123' && this.selectedProvince == 'เชียงราย'){  
        alert("Login successful");
        // this.$router.push("/system");
      } else {
        alert("Not successful");
      }
    },
    policy() {
      this.$router.push("/policy");
    },
    // filterProvinces() {
    //   this.filteredProvinces = this.provinces.filter((province) => {
    //     return (
    //       province.toLowerCase().indexOf(this.province.toLowerCase()) !== -1
    //     );
    //   });
    // },
    // provinceSelected(province) {
    //   this.province = province;
    //   this.filteredProvinces = [];
    // },
  },
};
</script>
