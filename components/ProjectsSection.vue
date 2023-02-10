<!-- eslint-disable vue/no-unused-vars -->
<template>
  <div
    class="bg-gradient-to-tr from-dark via-mediumDark to-glow text-white font-unbounded"
  >
    <div
      v-if="projects.data"
      class="grid grid-cols-3 gap-12 md:gap-4 lg:gap-8 container mx-auto px-6"
    >
      <h2 class="col-span-3">Projects</h2>
      <div
        v-for="project in projects.data"
        :key="project.id"
        class="col-span-3 md:col-span-1 flex flex-col h-full justify-between bg-mobileMenu px-4 py-4 rounded-3xl"
      >
        <div>
          <img
            class="rounded-tl-2xl rounded-tr-2xl"
            :src="
              'http://localhost:1337' +
              project.attributes.featuredImage.data.attributes.url
            "
          />
          <h3 class="pt-4 pb-2">{{ project.attributes.title }}</h3>
          <p>{{ project.attributes.shortDescription }}</p>
        </div>
        <div>
          <div class="flex flex-row flex-wrap gap-2 pt-4 pb-6">
            <SmallTags
              v-for="tag in project.attributes.technologies"
              :key="tag.id"
              class="text-xs"
              >{{ tag }}</SmallTags
            >
          </div>

          <PrimaryButton class="md:w-max px-12">View</PrimaryButton>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    projects: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
