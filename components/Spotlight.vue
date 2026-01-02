<script setup>
defineProps({
  x: { type: Number, default: 10 }, // Left position (%)
  y: { type: Number, default: 10 }, // Top position (%)
  w: { type: Number, default: 30 }, // Width of cutout (%)
  h: { type: Number, default: 20 }, // Height of cutout (%)
  active: { type: Boolean, default: false }, // Toggle the effect
});
</script>

<template>
  <div
    class="spotlight-cutout"
    :class="{ active }"
    :style="{
      top: y + '%',
      left: x + '%',
      width: w + '%',
      height: h + '%',
    }"
  ></div>
</template>

<style scoped>
.spotlight-cutout {
  position: absolute;
  z-index: 10; /* Ensure it sits on top of the image */
  pointer-events: none; /* Allows clicking 'through' the spotlight */

  /* Initial State (Invisible) */
  opacity: 0;
  box-shadow: 0 0 0 0 rgba(0, 0, 0, 0.7);

  /* Smoothly animate position and the fade-in */
  transition: opacity 0.5s ease, top 0.5s ease, left 0.5s ease, width 0.5s ease,
    height 0.5s ease;
}

.spotlight-cutout.active {
  opacity: 1;
  /* The Magic: A shadow so big it covers the container */
  /* 0 offset, 0 blur, spread radius 200vmax (huge) */
  box-shadow: 0 0 0 200vmax rgba(0, 0, 0, 0.7);
}
</style>
