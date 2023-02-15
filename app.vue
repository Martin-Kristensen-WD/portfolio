<template>
  <div>
    <NuxtLayout>
      <NuxtPage :page="page" :projects="projects" :experience="experience" />
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
