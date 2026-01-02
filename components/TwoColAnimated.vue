<script setup>
defineProps({
  active: {
    type: Boolean,
    default: false,
  },
});
</script>

<template>
  <div class="animated-grid h-full" :class="{ active }">
    <div class="description-col">
      <slot name="left"></slot>
    </div>

    <div class="image-col">
      <div class="image-wrapper">
        <slot name="right"></slot>
      </div>
    </div>
  </div>
</template>

<style scoped>
.animated-grid {
  display: grid;
  gap: 4px;
  grid-template-columns: 0fr 1fr;
  transition: grid-template-columns 0.5s ease-in-out;
}

.animated-grid.active {
  grid-template-columns: 1fr 4fr;
}

.description-col {
  /* Crucial for grid animation to work (allows shrinking to 0) */
  min-width: 0;
  min-height: 0;
  overflow: hidden;

  /* Layout for the content inside */
  display: flex;
  align-items: center;
  justify-content: center;

  flex-direction: column;
  gap: 1rem;
  font-size: 10px;
  /* width: 100%; Ensure text doesn't wrap prematurely */
  /* white-space: nowrap; Optional: prevents text reflow during anim */
}

.description-col :deep(ul) {
  padding-left: 0.4rem;
  margin: 0;
}

.animated-grid.active .description-col :deep(> :first-child) {
  transition: opacity 0.4s ease-out 0.4s;
}

.image-col {
  display: flex;
  align-items: center;
  justify-content: center;
}

.image-wrapper {
  position: relative;
  padding: 1rem;
  border-radius: 0.375rem; /* rounded-md */
  overflow: hidden;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}

/* Ensure images passed in scale correctly */
.image-wrapper :deep(img) {
  width: 100%;
  height: 100%;
  object-fit: contain;
}
</style>
