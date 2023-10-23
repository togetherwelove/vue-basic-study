<template>
  <ul>
    <li v-for="i in list" :key="i.id">{{ i.name }}: {{ i.age }}</li>
  </ul>
  {{ totalAge }}
</template>

<script setup>
import { computed, ref } from "vue";

const list = ref([
  { id: 1, name: "matthew", age: 20 },
  { id: 2, name: "juda", age: 30 },
  { id: 3, name: "alison", age: 43 },
  { id: 4, name: "dean", age: 62 },
]);

const calTotalAge = function () {
  return list.value.reduce((acc, cur) => acc + cur.age, 0);
};

const totalAge = computed(calTotalAge);
</script>
