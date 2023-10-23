<template>
  <button @click="increase">{{ count }}</button>
</template>

<script setup>
import { ref } from "vue";

const count = ref(0);

function increase() {
  count.value++;
}
</script>
