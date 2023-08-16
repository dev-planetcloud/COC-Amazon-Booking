<template>
  <div class="pl-6 pr-6 sm:pl-[20%] sm:pr-[20%]">
    <div class="pb-5">
      <div class="pb-3 text-[#333333] text-center">Privacy Policy</div>
      <span class="text-left text-[#333333] text-base font-extralight">
        nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat
        volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation
        ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.
        Lorem ipsum dolor sit amet, consectetuer adipiscing elit, sed diam
        nonummy nibh euismod tincidunt ut laoreet dolore magna aliquam erat
        volutpat. Ut wisi enim ad minim veniam, quis nostrud exerci tation
        ullamcorper suscipit lobortis nisl ut aliquip ex ea commodo consequat.
        Duis autem vel eum iriure dolor in hendrerit in vulputate velit esse
        molestie consequat, vel illum dolore eu feugiat nulla facilisis at vero
        eros et accumsan et iusto odio dignissim qui blandit praesent luptatum
        zzril delenit augue duis dolore te feugait nulla facilisi. Lorem ipsum
        dolor sit amet, cons commodo consequat. Duis autem vel eum iriure dolor
        in hendrerit in vulputate velit esse molestie consequat, vel illum
        dolore eu feugiat nulla facilisis at vero eros et accumsan et iusto odio
        dignissim qui blandit praesent luptatum zzril delenit augue duis dolore
        te feug
      </span>
    </div>

    <div class="flex justify-center">
      <div class="w-full sm:w-[25%] pt-0 sm:pt-[45%] sm:flex sm:justify-around">
        <div class="pt-2 sm:pt-0 text-center">
          <button
            class="bg-gradient-to-b from-cyan-500 to-teal-400 mb-3 inline-block w-full rounded px-6 sm:px-10 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-white shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
            type="submit"
            @click="accept_policy"
          >
            <span class="text-base">ยอมรับ</span>
          </button>
        </div>
        <div class="text-center">
          <button
            class="border-[1px] border-[#2AADCE] mb-3 inline-block w-full rounded px-6 sm:px-10 pt-2.5 pb-2 text-xs font-light uppercase leading-normal text-[#2AADCE] shadow-[0_4px_9px_-4px_rgba(0,0,0,0.2)] transition duration-150 ease-in-out hover:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)] focus:outline-none focus:ring-0 active:shadow-[0_8px_9px_-4px_rgba(0,0,0,0.1),0_4px_18px_0_rgba(0,0,0,0.2)]"
            type="button"
            @click="cancle"
          >
            <span class="text-base" >ปฏิเสธ</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    cancle() {
      this.$router.push("/login");
    },
    accept_policy() {
        this.$router.push('/register')
    }
  },
};
</script>