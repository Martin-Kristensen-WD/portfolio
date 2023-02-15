<template>
  <div
    class="bg-gradient-to-tr from-dark via-mediumDark to-glow text-white font-unbounded"
  >
    <div class="container mx-auto px-6 max-w-2xl">
      <p
        class="font-unbounded font-light uppercase text-base flex place-items-center"
      >
        <span class="pr-1"><img src="~/assets/icons/circles.svg" /></span>
        Latest Experience
      </p>
      <div v-for="exp in experience.data" :key="exp.id" class="py-6">
        <p class="py-5">{{ exp.attributes.date }}</p>
        <h4>{{ exp.attributes.job }}</h4>
        <p class="py-5">
          {{ exp.attributes.description }}
        </p>
        <NuxtLink :to="exp.attributes.link">
          <PrimaryButton class="md:w-max mt-4">Visit company</PrimaryButton>
        </NuxtLink>
      </div>
      <div class="grid place-items-center py-12">
        <p class="pb-6 md:text-lg">See full resume</p>
        <a
          v-if="page.data"
          :href="
            'http://localhost:1337' +
            page.data.attributes.cv.data.attributes.url
          "
        >
          <PrimaryButton>View CV</PrimaryButton>
        </a>
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
