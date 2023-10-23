<template>
  <input ref="inputTag" type="text" name="name" id="name" />
</template>

<script setup>
import { ref, onMounted } from "vue";

//Template Raf
const inputTag = ref();

//Lifecycle Hook
onMounted(() => {
  inputTag.value.focus();
});
</script>
