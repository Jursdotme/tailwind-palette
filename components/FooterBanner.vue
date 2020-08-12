<template>
  <transition name="fade">
    <div v-if="isVisible" class="fixed inset-x-0 bottom-0 pb-2 sm:pb-5">
      <div class="max-w-screen-xl px-2 mx-auto sm:px-6 lg:px-8">
        <div class="p-2 bg-indigo-600 rounded-lg shadow-lg sm:p-3">
          <div class="flex flex-wrap items-center justify-between">
            <div class="flex items-center flex-1 w-0">
              <span class="flex p-2 bg-indigo-800 rounded-lg">
                <svg
                  class="w-6 h-6 text-white"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M11 5.882V19.24a1.76 1.76 0 01-3.417.592l-2.147-6.15M18 13a3 3 0 100-6M5.436 13.683A4.001 4.001 0 017 6h1.832c4.1 0 7.625-1.234 9.168-3v14c-1.543-1.766-5.067-3-9.168-3H7a3.988 3.988 0 01-1.564-.317z"
                  />
                </svg>
              </span>
              <p class="ml-3 font-medium text-white truncate">
                <span class="md:hidden">
                  Still in development.
                </span>
                <span class="hidden md:inline">
                  Be gentle. This project is still in early development.
                </span>
              </p>
            </div>
            <div
              class="flex-shrink-0 order-3 w-full mt-2 sm:order-2 sm:mt-0 sm:w-auto"
            >
              <div class="rounded-md shadow-sm">
                <a
                  href="https://github.com/Jursdotme/tailwind-palette/projects/1"
                  class="flex items-center justify-center px-4 py-2 text-sm font-medium leading-5 text-indigo-600 transition duration-150 ease-in-out bg-white border border-transparent rounded-md hover:text-indigo-500 focus:outline-none focus:shadow-outline"
                >
                  Learn more
                </a>
              </div>
            </div>
            <div class="flex-shrink-0 order-2 sm:order-3 sm:ml-2">
              <button
                type="button"
                class="flex p-2 -mr-1 transition duration-150 ease-in-out rounded-md hover:bg-indigo-500 focus:outline-none focus:bg-indigo-500"
                aria-label="Dismiss"
                @click="isVisible = !isVisible"
              >
                <svg
                  class="w-6 h-6 text-white"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M6 18L18 6M6 6l12 12"
                  />
                </svg>
              </button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'FooterBanner',
  data() {
    return {
      isVisible: false
    }
  },
  created() {
    setTimeout(() => (this.isVisible = true), 3000)
  }
}
</script>

<style scoped>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>
