<template>
  <div
    class="bg-gradient-to-tr from-dark via-mediumDark to-glow text-white font-unbounded"
  >
    <div class="container mx-auto px-6 max-w-2xl">
      <p
        class="font-unbounded font-light uppercase text-base flex place-items-center"
      >
        <span class="pr-1"><img src="circles.svg" /></span>
        Featured jobs
      </p>
      <div v-if="experience.data">
        <div v-for="exp in experience.data" :key="exp.id" class="py-6">
          <p class="py-5">{{ exp.attributes.date }}</p>
          <h4>{{ exp.attributes.job }}</h4>
          <p class="py-5">
            {{ exp.attributes.description }}
          </p>
          <div class="flex flex-wrap gap-4">
            <NuxtLink
              :to="
                'http://localhost:1337' +
                exp.attributes.recommendation.data.attributes.url
              "
              target="__blank"
            >
              <PrimaryButton class="md:w-max mt-4"
                >Read recommendation</PrimaryButton
              >
            </NuxtLink>
            <NuxtLink :to="exp.attributes.link" target="__blank">
              <SecondaryButton class="md:w-max mt-4"
                >Visit company</SecondaryButton
              >
            </NuxtLink>
          </div>
        </div>
      </div>
      <div class="grid place-items-center py-12">
        <p class="pb-6 text-xl lg:text-2xl">See full resume</p>
        <NuxtLink
          v-if="page.data"
          :href="
            'http://localhost:1337' +
            page.data.attributes.cv.data.attributes.url
          "
          target="__blank"
        >
          <PrimaryButton>View resume</PrimaryButton>
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    experience: {
      type: Object,
      default: () => {},
    },
    page: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
