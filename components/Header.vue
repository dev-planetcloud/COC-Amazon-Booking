<template>
    <div>
      <nav
        class="fixed top-0 left-0 right-0 z-50 text-center text-2xl sm:text-2xl p-3 bg-white shadow text-[#26AFC8]"
      >
        <div class="relative">
          <div class="absolute">
            <button
              @click="backpage"
              class="cursor-pointer inline-flex items-center text-sm text-gray-500 rounded-lg hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400"
            >
              <fa
                :icon="['fas', 'angle-left']"
                class="text-3xl"
                style="color: #26afc8"
              />
            </button>
          </div>
        </div>
        Planet EV
      </nav>
    </div>
</template>



<script>
export default {
  data() {
    return {

    };
  },
  mounted() {},
  methods: {
    logout() {
      this.$router.push("/login");
    },
    backpage () {
      this.$router.go(-1);
    },
  },
};
</script>

<style>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 999;
  background-color: white;
  box-shadow: 0px 0px 5px rgba(0, 0, 0, 0.2);
}

.system-content {
  font-family: "Kanit", sans-serif;
}
</style>

