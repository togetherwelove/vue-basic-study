<template>
  <h1>AttributeBinding</h1>
  <p v-bind="attrs">{{ hello }}</p>
</template>

<script setup>
import { ref } from "vue";
const hello = ref("Hello world!");

const attrs = {
  id: "id",
  class: "class",
};
</script>

<style>
.class {
  color: blue;
}
</style>
