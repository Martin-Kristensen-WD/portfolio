<template>
  <div
    class="bg-gradient-to-tr from-dark via-mediumDark to-glow text-white font-unbounded"
  >
    <div
      class="container mx-auto grid grid-cols-3 place-items-center px-6 py-24"
    >
      <div class="col-span-3 md:col-span-2">
        <p
          class="font-unbounded font-light uppercase text-xs lg:text-base flex place-items-center"
        >
          <span class="pr-1"><img src="~/assets/icons/circles.svg" /></span>
          Latest Experience
        </p>
        <!-- {{ experience.data }} -->
        <p>May 2023 - November 2023</p>
        <h3>Checkmate</h3>
        <p>
          is simply dummy text of the printing and typesetting industry. Lorem
          Ipsum has been the industry's standard dummy text ever since the
          1500s, when an unknown printer took a galley of type and scrambled it
          to make a type specimen book. is simply dummy text of the printing and
          typesetting industry. Lorem Ipsum has been the industry's standard
          dummy text ever since the 1500s, when an unknown printer took a galley
          of type and scrambled it to make a type specimen book.
        </p>
        <PrimaryButton>Visit company</PrimaryButton>
      </div>
      <div class="col-span-3 md:col-span-1 place-items-center grid gap-4">
        <div class="h-10 w-10 rounded-full bg-primary"></div>
        <div class="h-8 w-px bg-lightGray mx-auto"></div>
        <div class="h-10 w-10 rounded-full bg-lightGray"></div>
        <div class="h-8 w-px bg-lightGray mx-auto"></div>
        <div class="h-10 w-10 rounded-full bg-lightGray"></div>
        <div class="h-8 w-px bg-lightGray mx-auto"></div>
        <div class="h-10 w-10 rounded-full bg-lightGray"></div>
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
  },
}
</script>
