<template>
  <div
    class="bg-gradient-to-br from-dark via-mediumDark to-glow text-white font-unbounded"
  >
    <div class="grid grid-cols-2 container mx-auto px-6 py-24">
      <div class="col-span-2 md:col-span-1">
        <h2>About me</h2>
        <img class="mb-12 md:pr-12 md:mb-0" src="~/assets/profile-pic.png" />
      </div>
      <p v-if="page.data" class="col-span-2 md:col-span-1 md:pt-8 md:pl-6">
        {{ page.data.attributes.aboutMe }}
        <PrimaryButton class="my-8">Download CV</PrimaryButton>
      </p>
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
