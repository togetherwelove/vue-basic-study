<template>
  <input v-model="name" />
  <br />
  <span>{{ errMsg }}</span>
</template>

<script setup>
import { ref, watch } from "vue";
const name = ref();
const errMsg = ref();

watch(name, (name) => {
  if (name.length >= 10) {
    errMsg.value = "10자를 초과합니다.";
  } else {
    errMsg.value = "";
  }
});
</script>
