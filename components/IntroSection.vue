<template>
  <div
    class="bg-gradient-to-br from-dark via-mediumDark to-glow h-screen text-white"
  >
    <div
      class="container mx-auto grid grid-cols-3 place-items-center md:place-items-end px-6 pt-6 md:pt-32"
    >
      <div class="col-span-3 md:col-span-2">
        <p
          v-if="page.data"
          class="font-unbounded font-light text-xs lg:text-base flex place-items-center"
        >
          <span class="pr-1"><img src="~/assets/icons/circles.svg" /></span>
          {{ page.data.attributes.tagline }}
        </p>
        <h1
          v-if="page.data"
          class="text-primary pt-4 pb-6 font-unbounded uppercase"
        >
          {{ page.data.attributes.headline }}
        </h1>
        <p v-if="page.data" class="md:pr-36">
          {{ page.data.attributes.introduction }}
        </p>
      </div>
      <!--       <div
        class="col-span-3 absolute bottom-6 flex items-center md:col-span-1 md:relative md:bottom-0 md:-mr-24"
      >
        <p class="mr-6 rotate-90">DISCOVER</p>
        <div class="w-px h-28 bg-white"></div>
      </div> -->
      <div>
        <!-- Lottie animation -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    page: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
