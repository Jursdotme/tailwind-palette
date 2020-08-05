<template>
  <div class="relative inline-block text-left">
    <div>
      <span class="rounded-md shadow-sm">
        <button
          id="options-menu"
          type="button"
          class="inline-flex justify-center w-full rounded-md border border-gray-300 px-4 py-2 bg-white text-sm leading-5 font-medium text-gray-700 hover:text-gray-500 focus:outline-none focus:border-blue-300 focus:shadow-outline-blue active:bg-gray-50 active:text-gray-800 transition ease-in-out duration-150"
          aria-haspopup="true"
          aria-expanded="true"
          @click="isOpen = !isOpen"
        >
          About this Project
          <svg
            class="-mr-1 ml-2 h-5 w-5"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
      </span>
    </div>

    <!--
    Dropdown panel, show/hide based on dropdown state.

    Entering: "transition ease-out duration-100"
      From: "transform opacity-0 scale-95"
      To: "transform opacity-100 scale-100"
    Leaving: "transition ease-in duration-75"
      From: "transform opacity-100 scale-100"
      To: "transform opacity-0 scale-95"
  -->
    <div
      v-show="isOpen"
      class="origin-top-right absolute right-0 mt-2 w-56 rounded-md shadow-lg"
    >
      <div
        class="rounded-md bg-white shadow-xs"
        role="menu"
        aria-orientation="vertical"
        aria-labelledby="options-menu"
      >
        <div class="px-4 py-3">
          <p class="text-sm leading-5">
            Made by
          </p>
          <p class="text-sm leading-5 font-medium text-gray-900 truncate">
            Rasmus Jürs
          </p>
        </div>
        <div class="border-t border-gray-100"></div>
        <div class="py-1">
          <a
            href="https:jurs.me"
            class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900"
            role="menuitem"
            >Website</a
          >
          <a
            href="https://github.com/Jursdotme"
            class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900"
            role="menuitem"
            >Github</a
          >
          <a
            href="https://codepen.io/Jursdotme"
            class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900"
            role="menuitem"
            >Codepen</a
          >
          <a
            href="https://twitter.com/jursdotme"
            class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900"
            role="menuitem"
            >Twitter</a
          >
          <a
            href="https://www.linkedin.com/in/rasmusjuers/"
            class="block px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900"
            role="menuitem"
            >Linked in</a
          >
        </div>
        <div class="border-t border-gray-100"></div>
        <div class="py-1">
          <form method="POST" action="#">
            <button
              type="submit"
              class="block w-full text-left px-4 py-2 text-sm leading-5 text-gray-700 hover:bg-gray-100 hover:text-gray-900 focus:outline-none focus:bg-gray-100 focus:text-gray-900"
              role="menuitem"
            >
              Contact
            </button>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  title: 'AboutButton',
  data() {
    return {
      isOpen: false
    }
  }
}
</script>

<style lang="scss" scoped></style>
