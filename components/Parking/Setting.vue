<template>
  <div class="h-full py-4 pt-0 sm:p-4 sm:pb-0">
    <div
      class="text-center sm:text-left items-center justify-center text-[#144779]"
    >
      <div class="justify-between flex">
        <span>ตั้งค่าการแจ้งเตือนไปยังผู้ใช้บริการ</span>
        <!-- <div>ประวัติการส่งข้อความ</div> -->
      </div>

      <div class="mt-3">
        <div>
          <div
            class="px-2 py-2 sm:px-4 bg-[#2BaDCF] text-white rounded-[6px] text-left"
          >
            <label class="text-sm lg:text-base sm:text-sm"
              >ตั้งค่าแจ้งเตือนการปิดให้บริการช่องจอดรถ</label
            >
          </div>
          <div class="px-2 py-2 sm:px-4 text-sm justify-between flex">
            <label class="text-[#A7A2A2] text-sm lg:text-base sm:text-sm"
              >กำหนดข้อความเพื่อส่งถึงผู้ใช้บริการ</label
            >
            <button
              @click="editable1 = !editable1"
              class="text-[#2BADCF] text-sm lg:text-base sm:text-sm"
            >
              {{ editable1 ? "บันทึก" : "แก้ไข" }}
            </button>
          </div>
          <textarea
            :readonly="!editable1"
            :class="{ 'bg-gray-200': !editable1 }"
            v-model="textData[0].t1"
            class="text-sm lg:text-base sm:text-sm w-full h-[9.5rem] px-2 py-2 sm:px-4 border border-[#B9B8B8] rounded-[10px] text-[#878484]"
          >
          </textarea>

          <div
            class="mt-4 px-2 py-2 sm:px-4 bg-[#2BaDCF] text-white rounded-[6px] text-left"
          >
            <label class="text-sm lg:text-base sm:text-sm"
              >ตั้งค่าแจ้งเตือนการปิดให้บริการช่องจอดรถ</label
            >
          </div>
          <div
            class="px-2 py-2 sm:px-4 text-[#A7A2A2] text-sm justify-between flex"
          >
            <label class="text-sm lg:text-base sm:text-sm"
              >กำหนดข้อความเพื่อส่งถึงผู้ใช้บริการ</label
            >
            <button
              @click="editable2 = !editable2"
              class="text-[#2BADCF] text-sm lg:text-base sm:text-sm"
            >
              {{ editable2 ? "บันทึก" : "แก้ไข" }}
            </button>
          </div>
          <textarea
            :readonly="!editable2"
            :class="{ 'bg-gray-200': !editable2 }"
            v-model="textData[0].t2"
            class="text-sm lg:text-base sm:text-sm w-full h-[9.5rem] px-2 py-2 sm:px-4 border border-[#B9B8B8] rounded-[10px] text-[#878484]"
          >
          </textarea>

          <div
            class="mt-4 px-2 py-2 sm:px-4 bg-[#2BaDCF] text-white rounded-[6px] text-left"
          >
            <label class="text-sm lg:text-base sm:text-sm"
              >ตั้งค่าแจ้งเตือนการปิดให้บริการช่องจอดรถ</label
            >
          </div>
          <div
            class="px-2 py-2 sm:px-4 text-[#A7A2A2] text-sm justify-between flex"
          >
            <label class="text-sm lg:text-base sm:text-sm"
              >กำหนดข้อความเพื่อส่งถึงผู้ใช้บริการ</label
            >
            <button
              @click="editable3 = !editable3"
              class="text-[#2BADCF] text-sm lg:text-base sm:text-sm"
            >
              {{ editable3 ? "บันทึก" : "แก้ไข" }}
            </button>
          </div>
          <textarea
            :readonly="!editable3"
            :class="{ 'bg-gray-200': !editable3 }"
            v-model="textData[0].t3"
            class="text-sm lg:text-base sm:text-sm w-full h-[9.5rem] px-2 py-2 sm:px-4 border border-[#B9B8B8] rounded-[10px] text-[#878484]"
          >
          </textarea>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      editable1: false,
      editable2: false,
      editable3: false,
      textData: [
        {
          t1: "Planet EV มีการปิดปรับปรุงช่องจอดชั่วคราวกรุณาจองเข้ามาใหม่อีกครั้ง ขออภัยในความไม่สะดวกขอบคุณค่ะ",
          t2: "เรียนผู้ใช้บริการ Planet EV Smart Parking  อีก 15 นาที จะถึงเวลาที่คุณได้จองใช้บริการช่องจอดรถ โปรดมาตามเวลานัดหมายด้วยค่ะ",
          t3: "เรียนผู้ใช้บริการ Planet EV Smart Parking  อีก 5 นาที จะสิ้นสุดเวลาการใช้บริการช่องจอดรถ ขอบคุณที่ใช้บริการค่ะ",
        },
      ],
    };
  },
};
</script>