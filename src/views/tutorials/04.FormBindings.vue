<template>
  <!-- <input type="text" :value="text" @input="onInput" placeholder="값을 입력하세요." /> -->
  <input type="text" v-model="text" placeholder="값을 입력하세요." />
  <p>{{ text }}</p>

  <hr />

  <input type="checkbox" id="checkbox" v-model="checked" />
  <label for="checkbox">{{ checked }}</label>

  <hr />

  <div>Checked names: {{ checkedNames }}</div>

  <input type="checkbox" id="jack" value="Jack" v-model="checkedNames" />
  <label for="jack">Jack</label>

  <input type="checkbox" id="john" value="John" v-model="checkedNames" />
  <label for="john">John</label>

  <input type="checkbox" id="mike" value="Mike" v-model="checkedNames" />
  <label for="mike">Mike</label>

  <hr />

  <div>Picked: {{ picked }}</div>

  <input type="radio" id="one" value="One" v-model="picked" />
  <label for="one">One</label>

  <input type="radio" id="two" value="Two" v-model="picked" />
  <label for="two">Two</label>
</template>
<script setup>
import { ref } from "vue";
const text = ref("text");
const checked = ref(false);
const checkedNames = ref([]);
const picked = ref("One");
// function onInput(e) { text.value = e.target.value; }
</script>
