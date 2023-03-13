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
                src="/menu-dots.svg"
              />
              <img
                class="transition duration-500 ease-in-out"
                :class="showMenu ? 'opacity-100' : 'opacity-0'"
                src="/x.svg"
              />
            </button>
          </div>
        </div>

        <div
          class="absolute top-0 left-0 w-screen h-screen bg-primaryHover transition duration-500 ease-in-out md:hidden"
          :class="showMenu ? 'opcaity-100' : 'opacity-0'"
        >
          <ul
            :class="showMenu ? 'flex' : 'hidden'"
            class="flex-col space-y-16 place-items-center mt-32"
          >
            <li
              class="text-lg hover:text-primary transition duration-300 ease-in-out"
              @click="
                $router.push({ name: 'index', hash: '#projects' }),
                  (showMenu = false)
              "
            >
              Projects
            </li>
            <li
              class="text-lg hover:text-primary transition duration-300 ease-in-out"
              @click="
                $router.push({ name: 'index', hash: '#about' }),
                  (showMenu = false)
              "
            >
              About
            </li>
            <li
              class="text-lg hover:text-primary transition duration-300 ease-in-out"
              @click="
                $router.push({ name: 'index', hash: '#footer' }),
                  (showMenu = false)
              "
            >
              Get in touch
            </li>
            <div class="flex gap-6 md:hidden">
              <a
                href="https://www.linkedin.com/in/kristensen-martin/"
                target="__blank"
              >
                <FooterSome> <img src="/linkedinLarge.svg" /></FooterSome>
              </a>
              <a
                href="https://github.com/Martin-Kristensen-WD"
                target="__blank"
              >
                <FooterSome> <img src="/githubLarge.svg" /></FooterSome>
              </a>
            </div>
          </ul>
        </div>

        <!-- Desktop menu -->
        <ul
          class="hidden md:flex flex-row items-center items-center space-x-20 cursor-pointer"
        >
          <button>
            <li
              class="text-base hover:text-primary transition duration-300 ease-in-out"
              @click="$router.push({ name: 'index', hash: '#projects' })"
            >
              Projects
            </li>
          </button>

          <li
            class="text-base hover:text-primary transition duration-300 ease-in-out"
            @click="$router.push({ name: 'index', hash: '#about' })"
          >
            About
          </li>

          <li
            class="text-base hover:text-primary transition duration-300 ease-in-out"
            @click="$router.push({ name: 'index', hash: '#footer' })"
          >
            Get in touch
          </li>
          <div class="flex gap-6 md:hidden">
            <a
              href="https://www.linkedin.com/in/kristensen-martin/"
              target="__blank"
            >
              <HeaderSoMe> <img src="/linkedin.svg" /></HeaderSoMe>
            </a>
            <a href="https://github.com/Martin-Kristensen-WD" target="__blank">
              <HeaderSoMe> <img src="/github.svg" /></HeaderSoMe>
            </a>
          </div>
        </ul>

        <!-- Desktop SoMe -->
        <div class="hidden md:flex md:gap-6">
          <a
            href="https://www.linkedin.com/in/kristensen-martin/"
            target="__blank"
          >
            <HeaderSoMe><img class="z-30" src="/linkedin.svg" /></HeaderSoMe>
          </a>
          <a href="https://github.com/Martin-Kristensen-WD" target="__blank">
            <HeaderSoMe><img class="z-30" src="/github.svg" /></HeaderSoMe>
          </a>
        </div>
      </nav>
    </div>
  </header>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const showMenu = ref(false)
    return {
      showMenu,
    }
  },
}
</script>
