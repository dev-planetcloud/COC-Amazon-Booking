<template>
  <div class="pl-6 pr-6 sm:pl-[20%] sm:pr-[20%]">
    <div class="pb-5">
      <div class="pb-3 text-[#333333] text-center text-2xl">
        ยืนยันตัวตนด้วย OTP
      </div>

      <form>
        <div class="mb-4 text-center">
          <div class="text-[#B0B0B0] text-base sm:text-xl font-light mb-4">
            รหัส OTP ได้ถูกส่งไปยังหมายเลข {{ otpphone }} กรุณาใส่หัส OTP
            ที่คุณได้รับ
          </div>
          <div class="text-[#1EB2C3]">{{ formattedTime }}</div>
        </div>
        <div
          id="otp"
          class="flex flex-row justify-center text-center px-2 mt-4"
        >
          <input
            v-model="otpInputs[0]"
            class="m-2 border h-10 w-10 text-center form-control rounded bg-[#F5F6F8]"
            type="text"
            id="first"
            maxlength="1"
          />
          <input
            v-model="otpInputs[1]"
            class="m-2 border h-10 w-10 text-center form-control rounded bg-[#F5F6F8]"
            type="text"
            id="second"
            maxlength="1"
          />
          <input
            v-model="otpInputs[2]"
            class="m-2 border h-10 w-10 text-center form-control rounded bg-[#F5F6F8]"
            type="text"
            id="third"
            maxlength="1"
          />
          <input
            v-model="otpInputs[3]"
            class="m-2 border h-10 w-10 text-center form-control rounded bg-[#F5F6F8]"
            type="text"
            id="fourth"
            maxlength="1"
          />
          <input
            v-model="otpInputs[4]"
            class="m-2 border h-10 w-10 text-center form-control rounded bg-[#F5F6F8]"
            type="text"
            id="fifth"
            maxlength="1"
          />
          <input
            v-model="otpInputs[5]"
            class="m-2 border h-10 w-10 text-center form-control rounded bg-[#F5F6F8]"
            type="text"
            id="sixth"
            maxlength="1"
          />
        </div>

        <div class="flex justify-center text-center mt-5 mb-20">
          <span class="text-[#B0B0B0]">ไม่ได้รับ OTP ? </span>
          <div
            class="flex items-center text-[#20B1C5] cursor-pointer"
            @click="sendOPT"
          >
            <span class="pl-2 underline"> ส่งอีกครั้ง</span>
          </div>
        </div>

        <div class="flex justify-center">
          <div class="w-full sm:w-[25%] pt-0 sm:flex sm:justify-around">
            <div class="pt-2 sm:pt-0 text-center">
              <button
                class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full rounded px-6 sm:px-10 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
                type="submit"
                @click="submitOTP"
              >
                <span class="text-base">ยืนยัน</span>
              </button>
            </div>
          </div>
        </div>
      </form>
      <div
        :class="{ hidden: !showAlert }"
        class="bg-gray-200 bg-opacity-75 absolute inset-0 flex items-center justify-center"
        @click="showAlert = false"
      >
        <div
          class="bg-white w-[30vh] sm:w-[35vh] md:w-80 lg:w-90 h-[26%] rounded-[4px]"
        >
          <div class="p-4 pt-6">
            <div class="flex items-center justify-center pb-6">
              <img src="../../assets/images/Ok.svg" />
            </div>
            <div class="text-center font-light mt-2">
              <span class="text-[#B0B0B0] text-base"
                >ส่งรหัส(OTP) ให้คุณเรียบร้อยแล้ว</span
              >
            </div>
          </div>
        </div>
      </div>

      <div
        :class="{ hidden: !showAlertCancle }"
        class="bg-gray-200 bg-opacity-75 absolute inset-0 flex items-center justify-center"
        @click="showAlertCancle = false"
      >
        <div
          class="bg-white w-[30vh] sm:w-[35vh] md:w-80 lg:w-90 h-[26%] rounded-[4px]"
        >
          <div class="p-4 pt-6">
            <div class="flex items-center justify-center pb-6">
              <img src="../../assets/images/Cancel.svg" />
            </div>
            <div class="text-center font-light mt-2">
              <span class="text-[#B0B0B0] text-base"
                >คุณใส่รหัส (OTP) ไม่ถูกต้องกรุณาใส่ใหม่อีกครั้ง</span
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      otpphone: "0222222",
      otp: "111111",
      timeLeft: 60,
      otpInputs: Array(6).fill(""),
      showAlert: false,
      showAlertCancle: false,
    };
  },
  mounted() {
    let countdown = setInterval(() => {
      this.timeLeft--;
      if (this.timeLeft === 0) {
        clearInterval(countdown);
      }
    }, 1000);

    const inputs = document.querySelectorAll("#otp input");
    inputs.forEach((input, index) => {
      input.addEventListener("input", (event) => {
        if (event.data !== null) {
          if (index < inputs.length - 1) {
            inputs[index + 1].focus();
          }
        }
      });
    });
  },
  computed: {
    formattedTime() {
      let minutes = Math.floor(this.timeLeft / 60);
      let seconds = this.timeLeft - minutes * 60;
      return `${minutes.toString().padStart(2, "0")} : ${seconds
        .toString()
        .padStart(2, "0")}`;
    },
  },
  methods: {
    submitOTP() {
      const inputtedOTP = this.otpInputs.join("");
      if (inputtedOTP === this.otp) {
        this.$router.push("/system");
      } else {
        this.showAlertCancle = true;
      }
    },
    sendOPT() {
      this.showAlert = true;
    },
    
  },
};
</script>