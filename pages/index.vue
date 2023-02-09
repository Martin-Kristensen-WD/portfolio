<template>
  <div>
    <div class="cursor"></div>
    <IntroSection />
    <ProjectsSection />
    <AboutSection />
    <TheFooter />
  </div>
</template>

<script>
export default {
  beforeMount() {
    const cursor = document.querySelector('.cursor')
    document.addEventListener('mousemove', function (e) {
      cursor.style.cssText =
        'left: ' + e.clientX + 'px; top: ' + e.clientY + 'px;'
    })
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
</style>
