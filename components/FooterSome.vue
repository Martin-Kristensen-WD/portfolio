<template>
  <div
    class="animation w-12 h-12 border border-white border-dashed rounded-full place-items-center grid cursor-pointer"
  >
    <slot></slot>
  </div>
</template>

<style>
.animation {
  transition: all 0.2s ease-in-out 0s;
  position: relative;
}

.animation:after {
  content: '';
  display: block;
  width: 90%;
  height: 90%;
  top: -20%;
  left: 0;
  right: 0;
  margin: auto;
  position: absolute;
  border-radius: 50%;
}

.animation:hover::after {
  top: 5%;
  transition: all 0.2s ease-in-out 0s;
  background-color: #ffa451;
}
</style>
