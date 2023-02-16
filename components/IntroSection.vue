<template>
  <div class="bg-gradient-to-br from-dark via-mediumDark to-glow text-white">
    <div
      class="container mx-auto grid grid-cols-3 place-items-center md:place-items-end px-6 py-6 md:py-12 lg:py-20"
    >
      <div class="col-span-3 lg:col-span-2">
        <p
          v-if="page.data"
          class="font-unbounded uppercase font-light text-base flex place-items-center"
        >
          <span class="pr-1"><img src="~/assets/icons/circles.svg" /></span>
          {{ page.data.attributes.tagline }}
        </p>
        <h1 v-if="page.data" class="text-primary pt-4 pb-6 font-unbounded">
          {{ page.data.attributes.headline }}
        </h1>
        <p v-if="page.data" class="md:pr-36">
          {{ page.data.attributes.introduction }}
        </p>
        <br />
        <p>
          I hope you’re having a great
          <span class="italic">{{ showDay() }}</span
          >!
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
  methods: {
    showDay() {
      const dateObj = new Date()
      const weekday = dateObj.toLocaleString('default', { weekday: 'long' })
      return weekday
    },
  },
}
</script>
