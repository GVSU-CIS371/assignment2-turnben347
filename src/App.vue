<template>
  <div>
    <h1>Build Your Beverage</h1>

    <!-- Base Beverage -->
    <label for="base">Base Beverage:</label>
    <select id="base" v-model="selectedBase">
      <option value="Coffee">Coffee</option>
      <option value="Green Tea">Green Tea</option>
      <option value="Black Tea">Black Tea</option>
    </select>

    <!-- Creamer -->
    <label for="creamer">Creamer:</label>
    <select id="creamer" v-model="selectedCreamer">
      <option value="No Creamer">No Creamer</option>
      <option value="Milk">Milk</option>
      <option value="Cream">Cream</option>
      <option value="Half & Half">Half & Half</option>
    </select>

    <!-- Syrup -->
    <label for="syrup">Syrup:</label>
    <select id="syrup" v-model="selectedSyrup">
      <option value="No Syrup">No Syrup</option>
      <option value="Vanilla">Vanilla</option>
      <option value="Caramel">Caramel</option>
      <option value="Hazelnut">Hazelnut</option>
    </select>

    <!-- Temperature -->
    <ul>
      <li v-for="temp in temps" :key="temp">
        <label>
          <input
            type="radio"
            name="temperature"
            :id="`r${temp}`"
            :value="temp"
            v-model="currentTemp"
          />
          {{ temp }}
        </label>
      </li>
    </ul>

    <!-- Beverage Display -->
    <Beverage
      :base="selectedBase"
      :creamer="selectedCreamer"
      :syrup="selectedSyrup"
      :isIced="currentTemp === 'Cold'"
    />
  </div>
</template>

<script setup lang="ts">
import Beverage from "./components/Beverage.vue";
import { ref } from "vue";
import { temps, currentTemp } from "./stores/beverage";

// New reactive state for selections
const selectedBase = ref("Coffee");
const selectedCreamer = ref("No Creamer");
const selectedSyrup = ref("No Syrup");
</script>

<style lang="scss">
body,
html {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 100%;
  background-color: #6e4228;
  background: linear-gradient(to bottom, #6e4228 0%, #956f5a 100%);
}
ul {
  list-style: none;
}
label {
  display: block;
  margin: 0.5rem 0;
  color: #fff;
}
select {
  margin-bottom: 1rem;
}
</style>
