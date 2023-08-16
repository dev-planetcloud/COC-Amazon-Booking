<template>
  <div class="pl-6 pr-6 sm:pl-[20%] sm:pr-[20%]">
    <div class="pb-5">
      <div class="pb-3 text-[#333333] text-left">ข้อมูลการลงทะเบียน</div>

      <form @submit.prevent="onSubmit">
        <div class="mb-4">
          <label for="name" class="text-sm font-light text-[#97A9AA]"
            >ชื่อ</label
          >
          <input
            class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-[4px] focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
            v-model="username"
          />
          <span v-if="showError && !username" class="text-red-500 text-xs"
            >กรุณากรอกข้อมูลให้ครบถ้วน</span
          >
        </div>
        <div class="mb-4">
          <label for="password" class="block text-sm font-light text-[#97A9AA]"
            >นามสกุล</label
          >
          <input
            class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-[4px] focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
            v-model="lastname"
          />
          <span v-if="showError && !lastname" class="text-red-500 text-xs"
            >กรุณากรอกข้อมูลให้ครบถ้วน</span
          >
        </div>
        <div class="mb-4">
          <label class="block text-sm font-light text-[#97A9AA]"
            >เบอร์โทรศัพท์</label
          >
          <input
            class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-[4px] focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
            type="phone"
            v-model="phone"
          />
          <span v-if="showError && !phone" class="text-red-500 text-xs"
            >กรุณากรอกข้อมูลให้ครบถ้วน</span
          >
        </div>
        <div class="mb-4">
          <label class="block text-sm font-light text-[#97A9AA]"
            >ทะเบียนรถ</label
          >
          <input
            class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-[4px] focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
            v-model="plate"
          />
          <span v-if="showError && !plate" class="text-red-500 text-xs"
            >กรุณากรอกข้อมูลให้ครบถ้วน</span
          >
        </div>
        <div class="mb-4">
          <label class="block text-sm font-light text-[#97A9AA]"
            >จังหวัดของทะเบียนรถคุณ</label
          >
          <!-- <input
            class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-[4px] focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
            v-model="province"
          /> -->

          <select
            id="province"
            class="shadow-sm bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-[4px] focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500 dark:shadow-sm-light"
            v-model="selectedProvince"
          >
            <option value="">-- เลือกจังหวัด --</option>
            <option
              v-for="province in provincesAll"
              :value="province"
              :key="province.id"
            >
              {{ province.provinceNameTh }}
            </option>
          </select>
          <span v-if="showError && !selectedProvince" class="text-red-500 text-xs"
            >กรุณากรอกข้อมูลให้ครบถ้วน</span
          >
        </div>
        <div class="mb-4">
          <label class="mb-4 block text-sm font-light text-[#97A9AA]"
            >Vehicle Types</label
          >

          <fieldset class="flex">
            <div class="flex items-center">
              <input
                id="country-option-1"
                type="radio"
                name="countries"
                class="w-4 h-4 border-gray-300 focus:ring-2 focus:ring-blue-300 dark:focus:ring-[#27AECB] dark:focus:bg-[#27AECB] dark:bg-gray-700 dark:border-gray-600"
                value="EV"
                checked
              />
              <label
                for="country-option-1"
                class="block ml-2 text-sm font-medium text-[#97A9AA]"
              >
                รถไฟฟ้า (EV)
              </label>
            </div>

            <div class="flex items-center pl-5">
              <input
                id="country-option-2"
                type="radio"
                name="countries"
                value="other"
                class="w-4 h-4 border-gray-300 focus:ring-2 focus:ring-blue-300 dark:focus:ring-blue-600 dark:focus:bg-blue-600 dark:bg-gray-700 dark:border-gray-600"
              />
              <label
                for="country-option-2"
                class="block ml-2 text-sm font-medium text-[#97A9AA]"
              >
                อื่นๆ
              </label>
            </div>
          </fieldset>
        </div>
        <div class="flex justify-center">
          <div class="w-full sm:w-[25%] pt-0 sm:flex sm:justify-around">
            <div class="pt-2 sm:pt-0 text-center">
              <button
                class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full rounded px-6 sm:px-10 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
                type="submit"
              >
                <span class="text-base">ยืนยันการลงทะเบียน</span>
              </button>
            </div>
          </div>
        </div>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      selectedProvince: "",
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
      username: "",
      lastname: "",
      phone: "",
      plate: "",
      province: "",
      submitted: false,
    };
  },
  computed: {
    showError() {
      return (
        this.submitted &&
        (!this.username ||
          !this.lastname ||
          !this.phone ||
          !this.plate ||
          !this.selectedProvince)
      );
    },
  },
  methods: {
    onSubmit() {
      this.submitted = true;
      if (
        this.username &&
        this.lastname &&
        this.phone &&
        this.plate &&
        this.selectedProvince
      ) {
        // complete form data is provided, redirect to new route
        this.$router.push("/otp");
      } else {
        // handle incomplete form data case
      }
    },
  },
};
</script>