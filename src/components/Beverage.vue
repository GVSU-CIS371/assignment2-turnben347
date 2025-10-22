<template>
  <Mug>
    <!-- Temperature layer -->
    <Cold v-if="isIced" />
    <Hot v-else />

    <Contents>
      <!-- Creamer layer only if selected -->
      <template v-slot:top>
        <Creamer v-if="creamer !== 'No Creamer'" :creamer="creamer" />
      </template>

      <!-- Syrup layer only if selected -->
      <template v-slot:mid>
        <Syrup v-if="syrup !== 'No Syrup'" :syrup="syrup" />
      </template>

      <!-- Base beverage is always shown -->
      <template v-slot:bottom>
        <Base :base="base" />
      </template>
    </Contents>
  </Mug>
</template>

<script setup lang="ts">
import Contents from "./Contents.vue";
import Mug from "./Mug.vue";
import Syrup from "./Syrup.vue";
import Base from "./Base.vue";
import Creamer from "./Creamer.vue";
import Hot from "./Hot.vue";
import Cold from "./Cold.vue";

type Props = {
  isIced: boolean;
  base: string;
  creamer: string;
  syrup: string;
};

defineProps<Props>();
</script>
