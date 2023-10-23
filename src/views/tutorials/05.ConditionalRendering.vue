<template>
  <!-- <template v-if="toggle"><h1>Hello World</h1></template> -->
  <div v-show="toggle"><h1>Hello World</h1></div>
  <button @click="toggleSwitch">switch</button>
</template>

<script setup>
import { ref } from "vue";
const toggle = ref(true);
function toggleSwitch() {
  toggle.value = !toggle.value;
}
</script>
