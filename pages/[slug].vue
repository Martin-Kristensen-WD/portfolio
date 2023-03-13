<template>
  <div>
    <TheHeader />
    <div
      v-if="project.data"
      class="bg-gradient-to-br from-dark via-mediumDark to-glow text-white"
    >
      <div
        class="container mx-auto grid grid-cols-3 gap-6 md:gap-x-16 px-6 pt-6"
      >
        <div class="col-span-3">
          <h1 class="text-primary py-2 font-unbounded lg:text-4xl">
            {{ project.data[0].attributes.title }}
          </h1>
        </div>
        <div class="col-span-3 md:col-span-2">
          <p>{{ project.data[0].attributes.description }}</p>
        </div>
        <div class="col-span-3 md:col-span-1">
          <p class="font-unbounded text-bold pb-6">Technologies</p>
          <div class="flex flex-row flex-wrap gap-4">
            <LargeTags
              v-for="tag in project.data[0].attributes.technologies"
              :key="tag.id"
              class="text-base"
              >{{ tag }}</LargeTags
            >
          </div>

          <PrimaryButton v-if="project.data[0].attributes.URL" class="mt-12"
            ><a :href="project.data[0].attributes.URL" target="_blank"
              >View online</a
            ></PrimaryButton
          >
        </div>
      </div>
      <!--  {{ project.data[0].attributes }} -->
      <!-- IMAGES -->
      <div
        class="grid grid-cols-12 gap-6 container px-6 mx-auto pt-12 md:pt-20"
      >
        <div
          v-if="project.data"
          class="col-span-12 md:col-span-5 bg-image h-40 md:h-64 lg:h-96"
          :style="
            'background-image: url(' +
            project.data[0].attributes.images.data[0].attributes.url +
            ');'
          "
        ></div>
        <div
          v-if="project.data"
          class="col-span-12 md:col-span-7 bg-image h-40 md:h-64 lg:h-96"
          :style="
            'background-image: url(' +
            project.data[0].attributes.images.data[1].attributes.url +
            ');'
          "
        ></div>
        <div
          v-if="
            project.data[0].attributes.images.data[2] &&
            project.data[0].attributes.images.data.length > 2
          "
          class="col-span-12 md:col-span-7 bg-image h-40 md:h-64 lg:h-96"
          :style="
            'background-image: url(' +
            project.data[0].attributes.images.data[2].attributes.url +
            ');'
          "
        ></div>
        <div
          v-if="
            project.data[0].attributes.images.data[3] &&
            project.data[0].attributes.images.data.length > 2
          "
          class="col-span-12 md:col-span-5 bg-image h-40 md:h-64 lg:h-96"
          :style="
            'background-image: url(' +
            project.data[0].attributes.images.data[3].attributes.url +
            ');'
          "
        ></div>
        <!---->
      </div>

      <div class="py-12 lg:py-20">
        <button
          class="mx-auto bg-primary px-6 py-3 grid place-items-center rounded-full font-light font-unbounded text-sm hover:bg-primaryHover transition duration-500 ease-in-out"
          @click="$router.push({ name: 'index', hash: '#projects' })"
        >
          To projects
        </button>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const project = ref({})

    function parseJSON(resp) {
      return resp.json ? resp.json() : resp
    }

    function checkStatus(resp) {
      if (resp.status >= 200 && resp.status < 300) {
        return resp
      }
      return this.parseJSON(resp).then((resp) => {
        throw resp
      })
    }

    onMounted(async () => {
      const { slug } = useRoute().params
      try {
        const response = await fetch(
          `https://mk-portfolio-backend.herokuapp.com/api/projects?filters[slug][$eq]=${slug}&populate=*`,
          {
            method: 'GET',
          }
        )
          .then(checkStatus)
          .then(parseJSON)
        project.value = response
      } catch (error) {
        console.log(error)
      }
    })

    return {
      project,
    }
  },
}
</script>
