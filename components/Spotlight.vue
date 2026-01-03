<script setup>
import { computed } from 'vue';

const props = defineProps({
  x: { type: Array, default: () => [10] }, // Left position (%)
  y: { type: Array, default: () => [10] }, // Top position (%)
  w: { type: Array, default: () => [30] }, // Width of cutout (%)
  h: { type: Array, default: () => [20] }, // Height of cutout (%)
  activeClicks: { type: Array, default: () => [1] }, // Toggle the effect
});

const active = computed(() => props.activeClicks.includes($clicks.value))

const idx = computed(() => {
  const idx = props.activeClicks.indexOf($clicks.value)
  if (idx !== -1) return idx;

  // return the index of the next smaller element
  // assume that the array is sorted, starting with the smallest element
  return props.activeClicks.reduce((acc, val, idx) => {
    if (val < $clicks.value) return idx;

    return acc;
  }, 0);
})

</script>

<template>
  <div
    class="spotlight-cutout"
    :class="{ active }"
    :style="{
      top: y[idx] + '%',
      left: x[idx] + '%',
      width: w[idx] + '%',
      height: h[idx] + '%',
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
  /*A shadow so big it covers the container */
  /* 0 offset, 0 blur, spread radius 200vmax (huge) */
  box-shadow: 0 0 0 200vmax rgba(0, 0, 0, 0.7);

  /* Smoothly animate position and the fade-in */
  transition: opacity 0.5s ease, top 0.5s ease, left 0.5s ease, width 0.5s ease,
    height 0.5s ease;
}

.spotlight-cutout.active {
  opacity: 1;
}
</style>
