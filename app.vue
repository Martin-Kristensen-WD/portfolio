<template>
  <div>
    <NuxtLayout>
      <NuxtPage :page="page" :projects="projects" :experience="experience" />
      <div class="cursor"></div>
    </NuxtLayout>
  </div>
</template>

<script>
export default {
  data() {
    return {
      page: {},
      projects: {},
      experience: {},
      error: null,
      headers: { 'Content-Type': 'application/json' },
    }
  },
  async mounted() {
    try {
      const response = await fetch(
        'http://localhost:1337/api/page?populate=*',
        {
          method: 'GET',
          headers: this.headers,
        }
      )
        .then(this.checkStatus)
        .then(this.parseJSON)
      this.page = response
    } catch (error) {
      this.error = error
    }

    try {
      const response2 = await fetch(
        'http://localhost:1337/api/projects?populate=*',
        {
          method: 'GET',
          headers: this.headers,
        }
      )
        .then(this.checkStatus)
        .then(this.parseJSON)
      this.projects = response2
    } catch (error) {
      this.error = error
    }

    try {
      const response3 = await fetch(
        'http://localhost:1337/api/experiences?populate=*&sort=createdAt:ASC',
        {
          method: 'GET',
          headers: this.headers,
        }
      )
        .then(this.checkStatus)
        .then(this.parseJSON)
      this.experience = response3
    } catch (error) {
      this.error = error
    }

    const cursor = document.querySelector('.cursor')
    document.addEventListener('mousemove', function (e) {
      cursor.style.cssText =
        'left: ' + e.clientX + 'px; top: ' + e.clientY + 'px;'
    })
  },

  methods: {
    parseJSON: function (resp) {
      return resp.json ? resp.json() : resp
    },
    checkStatus: function (resp) {
      if (resp.status >= 200 && resp.status < 300) {
        return resp
      }
      return this.parseJSON(resp).then((resp) => {
        throw resp
      })
    },
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
