<template>
  <ChildComp :msg="greeting" @response="who" />
</template>

<script setup>
import { ref } from "vue";
import ChildComp from "./ChildComp.vue";

let greeting = ref("Hello");

const who = function (name) {
  greeting.value = name;
};
</script>
