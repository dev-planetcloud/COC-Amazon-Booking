<template>
  <div class="h-full flex mt-1">
    <div class="flex justify-between w-full">
      <div class="flex flex-col h-full w-[35%] text-center text-[#0F3157]">
        <div
          class="flex-grow border-t-2 border-l-2 border-b-2 border-dotted flex items-center justify-center  cursor-pointer"
          @click="p1n = !p1n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p1n },
            ]"
          >
            P1 -
            <p class="text-[#008890] pl-1" :class="{ 'text-red-500': !p1n }">
              {{ p1n ? "AC" : "AC Close" }}
            </p>
          </div>
        </div>
        <div
          class="flex-grow border-l-2 border-b-2 border-dotted flex items-center justify-center  cursor-pointer"
          @click="p2n = !p2n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p2n },
            ]"
          >
            P2 -
            <p class="text-[#008890] pl-1" :class="{ 'text-red-500': !p2n }">
              {{ p2n ? "AC" : "AC Close" }}
            </p>
          </div>
        </div>
        <div
          class="flex-grow border-l-2 border-b-2 border-dotted flex items-center justify-center  cursor-pointer"
          @click="p3n = !p3n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p3n },
            ]"
          >
            P3 -
            <p class="text-[#008890] pl-1" :class="{ 'text-red-500': !p3n }">
              {{ p3n ? "DC" : "DC Close" }}
            </p>
          </div>
        </div>

        <div
          class="flex-grow border-l-2 border-b-2 border-dotted flex items-center justify-center  cursor-pointer"
          @click="p4n = !p4n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p4n },
            ]"
          >
            P4 -
            <p class="text-[#008890] pl-1" :class="{ 'text-red-500': !p4n }">
              {{ p4n ? "DC" : "DC Close" }}
            </p>
          </div>
        </div>
        <div
          class="flex-grow border-l-2 border-b-2 border-dotted flex items-center justify-center  cursor-pointer"
          @click="p5n = !p5n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p5n },
            ]"
          >
            P5 -
            <p class="text-[#008890] pl-1" :class="{ 'text-red-500': !p5n }">
              {{ p5n ? "DC" : "DC Close" }}
            </p>
          </div>
        </div>
        <div
          class="flex-grow border-l-2 border-b-2 border-dotted flex items-center justify-center cursor-pointer"
          @click="p6n = !p6n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p6n },
            ]"
          >
            P6 -
            <p class="text-[#008890] pl-1" :class="{ 'text-red-500': !p6n }">
              {{ p6n ? "DC" : "DC Close" }}
            </p>
          </div>
        </div>
      </div>

      <div class="text-[#D3D3D7] text-2xl font-extralight pt-5">ทางเข้า</div>

      <div class="flex flex-col h-full w-[35%] text-center text-[#0F3157]">
        <div
          class="flex-grow border-t-2 border-r-2 border-b-2 border-dotted flex items-center justify-center text-sm lg:text-xl sm:text-sm cursor-pointer"
        >
          P7 - Public
        </div>
        <div
          class="flex-grow border-r-2 border-b-2 border-dotted flex items-center justify-center text-sm lg:text-xl sm:text-sm cursor-pointer"
        >
          P8 - Public
        </div>
        <div
          class="flex-grow border-r-2 border-b-2 border-dotted flex items-center justify-center text-sm lg:text-xl sm:text-sm cursor-pointer"
        >
          P9 - Public
        </div>
        <div
          class="flex-grow border-r-2 border-b-2 border-dotted flex items-center justify-center text-sm lg:text-xl sm:text-sm cursor-pointer"
        >
          P10 - Public
        </div>
        <div
          class="flex-grow border-r-2 border-b-2 border-dotted flex items-center justify-center text-sm lg:text-xl sm:text-sm cursor-pointer"
        >
          P11 - Public
        </div>
        <div
          class="flex-grow border-r-2 border-b-2 border-dotted flex items-center justify-center cursor-pointer "
          @click="p12n = !p12n"
        >
          <div
            class="flex"
            :class="[
              'flex',
              'items-center',
              'justify-center',
              'text-sm lg:text-xl sm:text-sm',
              'cursor-pointer',
              { 'bg-gray-300 rounded-[10px] h-4/5 w-[90%] lg:w-4/5': !p12n },
            ]"
          >
            P12 -
            <p class="text-[#0F3157] pl-1" :class="{ 'text-red-500': !p12n }">
              {{ p12n ? "Public" : "Close" }}
            </p>
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
      p1n: true,
      p2n: true,
      p3n: true,
      p4n: true,
      p5n: true,
      p6n: true,
      p12n: true,

      check:[
        {
            id:1,
            status:'book',
            p1n: true,
        },
        {
            id:2,
            status:'park',
            p1n: true,
        },
        {
            id:3,
            status:'blank',
            p1n: true,
        },
        {
            id:4,
            status:'book',
            p1n: true,
        },
      ]
    };
  },
};
</script>
