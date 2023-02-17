<template>
  <div
    class="bg-gradient-to-br from-dark via-mediumDark to-glow text-white font-unbounded"
  >
    <div id="about" class="grid grid-cols-2 container mx-auto px-6 py-24">
      <div class="col-span-2 md:col-span-1">
        <h2>About me</h2>
        <img class="mb-12 md:pr-12 md:mb-0" src="/profile-pic.png" />
      </div>
      <div
        v-if="page.data"
        class="col-span-2 md:col-span-1 md:pt-16 md:pl-6 grid gap-y-5"
      >
        <p v-if="page.data.attributes.about1">
          {{ page.data.attributes.about1 }}
        </p>
        <p v-if="page.data.attributes.about2">
          {{ page.data.attributes.about2 }}
        </p>
        <p v-if="page.data.attributes.about3">
          {{ page.data.attributes.about3 }}
        </p>
        <p v-if="page.data.attributes.about4">
          {{ page.data.attributes.about4 }}
        </p>
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
