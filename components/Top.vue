<template>
  <nav
    class="bg-blue-600 text-white border-gray-200 px-2 sm:px-4 py-2.5 dark:bg-gray-800"
  >
    <div class="container flex flex-wrap justify-between items-center mx-auto">
      <a href="#" class="flex">
        <span
          class="self-center text-lg font-semibold whitespace-nowrap dark:text-white"
          >Tailwind Block</span
        >
      </a>
      <div class="w-full md:block md:w-auto">
        <ul
          class="flex flex-col mt-4 md:flex-row md:space-x-8 md:mt-0 md:text-sm md:font-medium"
        >
          <li>
            <a
              href="#"
              class="block py-2 pr-4 pl-3 text-white rounded dark:text-white"
              aria-current="page"
              >Code</a
            >
          </li>
          <li>
            <a
              href="#"
              class="block py-2 pr-4 pl-3 text-white rounded dark:text-white"
              aria-current="page"
              >Color</a
            >
          </li>
          <li>
            <a
              href="#"
              class="block py-2 pr-4 pl-3 text-white rounded dark:text-white"
              aria-current="page"
              >View</a
            >
          </li>
          <li>
            <!-- Toggle B -->
            <div class="flex items-center justify-center w-full">
              <label for="toggleB" class="flex items-center cursor-pointer">
                <!-- toggle -->
                <div class="relative">
                  <!-- input -->
                  <input
                    type="checkbox"
                    id="toggleB"
                    class="sr-only"
                    v-model="isChecked"
                    @change="changeMode()"
                    
                  />
                  <!-- line -->
                  <div class="block bg-gray-600 w-14 h-8 rounded-full"></div>
                  <!-- dot -->
                  <div
                    class="dot absolute left-1 top-1 bg-white w-6 h-6 rounded-full transition"
                  ></div>
                </div>
                
              </label>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  data() {
    return {
      isChecked: false,
      isDark: false,
    };
  },

  mounted() {
    if (JSON.parse(localStorage.getItem("mode")) === null) {
      this.isDark = false;
      this.isChecked = false;
      localStorage.setItem("mode", this.isDark);
    }

    if (JSON.parse(localStorage.getItem("mode")) == true) {
      document.body.classList.add("dark");
      this.isDark = true;
      this.isChecked = true;
      localStorage.setItem("mode", this.isDark);
    }

    if (JSON.parse(localStorage.getItem("mode")) == false) {
      document.body.classList.remove("dark");
      this.isDark = false;
      this.isChecked = false;
      localStorage.setItem("mode", this.isDark);
      console.log(JSON.parse(localStorage.getItem("mode")));
    }
  },

  methods: {
    changeMode() {
      if (this.isDark == true) {
        this.isDark = false;
        localStorage.setItem("mode", this.isDark);
        document.body.classList.remove("dark");
      } else {
        this.isDark = true;
        localStorage.setItem("mode", this.isDark);
        document.body.classList.add("dark");
      }
    },
  },
};
</script>

<style>
/* Toggle B */
input:checked ~ .dot {
  transform: translateX(100%);
  background-color: #000;
}
</style>
