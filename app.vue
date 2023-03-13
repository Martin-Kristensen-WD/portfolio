<template>
  <div>
    <NuxtLayout>
      <NuxtPage :page="page" :projects="projects" :experience="experience" />
      <div class="cursor"></div>
    </NuxtLayout>
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  setup() {
    const page = ref({})
    const projects = ref({})
    const experience = ref({})

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
      try {
        const response = await fetch(
          'https://mk-portfolio-backend.herokuapp.com/api/page?populate=*',
          {
            method: 'GET',
          }
        )
          .then(checkStatus)
          .then(parseJSON)
        page.value = response
      } catch (error) {
        console.log(error)
      }

      try {
        const response2 = await fetch(
          'https://mk-portfolio-backend.herokuapp.com/api/projects?populate=*',
          {
            method: 'GET',
          }
        )
          .then(checkStatus)
          .then(parseJSON)
        projects.value = response2
      } catch (error) {
        console.log(error)
      }

      try {
        const response3 = await fetch(
          'https://mk-portfolio-backend.herokuapp.com/api/experiences?populate=*&sort=createdAt:ASC',
          {
            method: 'GET',
          }
        )
          .then(checkStatus)
          .then(parseJSON)
        experience.value = response3
      } catch (error) {
        console.log(error)
      }

      const cursor = document.querySelector('.cursor')
      document.addEventListener('mousemove', function (e) {
        cursor.style.cssText =
          'left: ' + e.clientX + 'px; top: ' + e.clientY + 'px;'
      })
    })

    return {
      page,
      projects,
      experience,
    }
  },
}
</script>

<style>
.cursor {
  position: fixed;
  left: 0;
  top: 0;
  width: 40px;
  height: 40px;
  border: 1px solid #fff;
  border-radius: 50%;
  pointer-events: none;
  transform: translate(-50%, -50%);
}

@media only screen and (max-width: 1000px) {
  .cursor {
    display: none;
  }
}

.page-enter-active,
.page-leave-active {
  transition-property: opacity;
  transition-timing-function: ease-in-out;
  transition-duration: 250ms;
}
.page-enter-from,
.page-leave-to {
  opacity: 0;
}
</style>
