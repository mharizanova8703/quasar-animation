<template>
  <div class="squirrel" ref="squirrelRef">
    <img src="squirrel.png" alt="squirrel" />
  </div>
</template>

<script setup>
import { ref, defineExpose } from "vue";

// Create a single ref for this squirrel
const squirrelRef = ref(null);

defineExpose({
  squirrelRef
});
</script>

<style scoped lang="scss">
.squirrel {
  position: absolute;
  top: 0; /* Top of card */
  left: 50%;
  transform: translateX(-50%);
  width: 120px;
  opacity: 0;
  pointer-events: none;
  z-index: 10;
}

.squirrel img {
  width: 100%;
}
</style>
