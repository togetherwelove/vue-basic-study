<template>
  <ChildComp :msg="greeting" />
</template>

<script setup>
import { ref } from "vue";
import ChildComp from "../views/tutorials/ChildComp.vue";

const greeting = ref("Hello");
</script>
