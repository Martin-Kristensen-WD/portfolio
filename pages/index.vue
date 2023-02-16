<!-- eslint-disable prettier/prettier -->
<template>
  <div>
    <TheHeader />
    <IntroSection :page="page" />
    <ProjectsSection :projects="projects" />
    <AboutSection :page="page" />
    <ExperienceSection :experience="experience" :page="page" />
    <TheFooter />
  </div>
</template>

<script>
export default {
  props: {
    page: {
      type: Object,
      default: () => {},
    },
    projects: {
      type: Object,
      default: () => {},
    },
    experience: {
      type: Object,
      default: () => {},
    },
  },
}
</script>
