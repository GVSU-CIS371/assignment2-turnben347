<template>
  <div :class="baseClass"></div>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{ base: string }>();

// Compute a class based on selected base beverage
const baseClass = computed(() => {
  switch (props.base) {
    case "Coffee":
      return "baseBeverage coffee";
    case "Green Tea":
      return "baseBeverage greenTea";
    case "Black Tea":
      return "baseBeverage blackTea";
    default:
      return "baseBeverage";
  }
});
</script>

<style scoped>
.baseBeverage {
  position: relative;
  width: 100%;
  height: 100%;
  bottom: 0;
  animation: pour-tea 2s;
  z-index: 300;
  border-radius: 0.05em 0.05em 2.2em 2.2em;
}

/* Dynamic colors */
.coffee {
  background-color: #6f4e37; /* brown */
}

.greenTea {
  background-color: #d0f0c0; /* light green */
}

.blackTea {
  background-color: #3b2f2f; /* dark brown */
}

/* Optional pour animation */
@keyframes pour-tea {
  0% {
    height: 0%;
  }
  100% {
    height: 100%;
  }
}
</style>
