<template>
  <div class="syrup" :class="syrupClass"></div>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{ syrup: string }>();

const syrupClass = computed(() => {
  switch (props.syrup) {
    case "Vanilla":
      return "vanilla";
    case "Caramel":
      return "caramel";
    case "Hazelnut":
      return "hazelnut";
    default:
      return "";
  }
});
</script>

<style lang="scss" scoped>
.syrup {
  transform: translateY(400%);
  position: relative;
  width: 100%;
  height: 20%;
  animation: pour-tea 2s 1s forwards;
  z-index: 2;
}

/* Syrup colors */
.syrup.vanilla {
  background-color: #f3e5ab; /* pale yellow */
}

.syrup.caramel {
  background-color: #c68e17; /* caramel brown */
}

.syrup.hazelnut {
  background-color: #a0522d; /* hazelnut brown */
}
</style>
