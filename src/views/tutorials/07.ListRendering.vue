<template>
  <div class="group">
    <input v-model="newTodo" />
    <button @click="addTodo">add</button>
  </div>
  <span v-for="i in 10" :key="i">{{ i }}</span>
  <ul>
    <li v-for="(todo, key, i) in todos" :key="i">
      {{ todo }} - {{ key }} -
      {{ i }}
    </li>
  </ul>
</template>

<script setup>
import { ref, reactive } from "vue";

let id = 1;

let newTodo = ref("");

function addTodo() {
  todos.value.push({ id: id++, title: newTodo.value });
  newTodo.value = "";
}

const todos = reactive({
  id: id++,
  title: "learn Java",
  author: "James Gosling",
});
</script>
