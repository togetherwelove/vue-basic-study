<template>
  <h2>{{ msg }}</h2>
</template>

<script setup>
defineProps({
  msg: String,
});

const emit = defineEmits(["response"]);

emit("response", "Dean");
</script>
