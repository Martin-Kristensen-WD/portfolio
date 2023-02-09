<template>
  <header>
    <div class="bg-gradient-to-r from-dark to-mediumDark">
      <nav
        class="container text-white px-6 py-8 mx-auto md:flex md:justify-between md:items-center font-unbounded"
      >
        <div class="flex justify-between">
          <NuxtLink to="/" class="text-xl font-bold md:text-2xl">MK </NuxtLink>
          <!-- Mobile menu button -->
          <div class="flex md:hidden relative" @click="showMenu = !showMenu">
            <button type="button" class="z-50 focus:outline-none">
              <img
                class="absolute left-0 transition duration-500 ease-in-out"
                :class="showMenu ? 'opacity-0' : 'opacity-100'"
                src="~/assets/icons/menu-dots.svg"
              />
              <img
                class="transition duration-500 ease-in-out"
                :class="showMenu ? 'opacity-100' : 'opacity-0'"
                src="~/assets/icons/X.svg"
              />
            </button>
          </div>
        </div>

        <div
          class="absolute top-0 left-0 w-screen h-screen bg-mobileMenu transition duration-500 ease-in-out md:hidden"
          :class="showMenu ? 'opcaity-100' : 'opacity-0'"
        >
          <ul
            :class="showMenu ? 'flex' : 'hidden'"
            class="flex-col space-y-16 place-items-center mt-32"
          >
            <NuxtLink to="https://nuxtjs.org"
              ><li
                class="text-base hover:text-primary transition duration-300 ease-in-out"
              >
                Projects
              </li></NuxtLink
            >
            <NuxtLink to="https://nuxtjs.org"
              ><li
                class="text-base hover:text-primary transition duration-300 ease-in-out"
              >
                About
              </li></NuxtLink
            >
            <NuxtLink to="https://nuxtjs.org"
              ><li
                class="text-base hover:text-primary transition duration-300 ease-in-out"
              >
                Get in touch
              </li></NuxtLink
            >
            <div class="flex gap-6 md:hidden">
              <HeaderSoMe>
                <img src="~/assets/icons/linkedin.svg"
              /></HeaderSoMe>
              <HeaderSoMe> <img src="~/assets/icons/github.svg" /></HeaderSoMe>
            </div>
          </ul>
        </div>

        <!-- Desktop menu -->
        <ul
          class="hidden md:flex flex-row items-center items-center space-x-20 cursor-pointer"
        >
          <NuxtLink to="https://nuxtjs.org"
            ><li
              class="text-base hover:text-primary transition duration-300 ease-in-out"
            >
              Projects
            </li></NuxtLink
          >
          <NuxtLink to="https://nuxtjs.org"
            ><li
              class="text-base hover:text-primary transition duration-300 ease-in-out"
            >
              About
            </li></NuxtLink
          >
          <NuxtLink to="https://nuxtjs.org"
            ><li
              class="text-base hover:text-primary transition duration-300 ease-in-out"
            >
              Get in touch
            </li></NuxtLink
          >
          <div class="flex gap-6 md:hidden">
            <HeaderSoMe>
              <img src="~/assets/icons/linkedinHeader.svg"
            /></HeaderSoMe>
            <HeaderSoMe> <img src="~/assets/icons/github.svg" /></HeaderSoMe>
          </div>
        </ul>

        <!-- Desktop SoMe -->
        <div class="hidden md:flex md:gap-6">
          <HeaderSoMe
            ><img class="z-30" src="~/assets/icons/linkedinHeader.svg"
          /></HeaderSoMe>
          <HeaderSoMe
            ><img class="z-30" src="~/assets/icons/github.svg"
          /></HeaderSoMe>
        </div>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      showMenu: false,
    }
  },
}
</script>
