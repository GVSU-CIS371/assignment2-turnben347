<template>
  <div class="froth" :class="creamerClass">
    <div v-for="n in 5" :key="n" class="foam"></div>
  </div>
</template>

<script setup lang="ts">
import { computed } from "vue";

const props = defineProps<{ creamer: string }>();

// Compute a class based on selected creamer
const creamerClass = computed(() => {
  switch (props.creamer) {
    case "Milk":
      return "milk";
    case "Cream":
      return "cream";
    case "Half & Half":
      return "halfhalf";
    default:
      return "";
  }
});
</script>

<style lang="scss" scoped>
.froth {
  overflow: visible;
  transform: translateY(400%);
  position: relative;
  height: 20%;
  width: 100%;
  animation: pour-tea 2s 2s forwards;
}

.foam {
  display: block;
  border-radius: 30px;
  height: 40px;
  width: 40px;
  position: absolute;
}

.foam:nth-child(1) { top: 0px; left: -3px; }
.foam:nth-child(2) { top: 0px; left: 55px; }
.foam:nth-child(3) { width: 30px; height: 30px; border-radius: 40px; top: 3px; left: 30px; }
.foam:nth-child(4) { width: 30px; height: 30px; border-radius: 45px; top: 5px; right: -2px; }
.foam:nth-child(5) { top: 2px; right: 10px; }

/* Dynamic creamer colors */
.froth.milk { background-color: #f5f5dc; }       /* light beige */
.froth.cream { background-color: #fffdd0; }      /* cream */
.froth.halfhalf { background: linear-gradient(#f5f5dc, #fffdd0); } /* gradient */
</style>
