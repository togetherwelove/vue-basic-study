<template>
  <v-container>
    <v-row>
      <v-col>
        <v-select v-model="filterPrice" :items="priceItem" item-title="label" item-value="price" label="가격" return-object> </v-select>
      </v-col>
      <v-col>
        <v-select v-model="sortProp" :items="sortItem" item-title="title" item-value="method" label="정렬" return-object> </v-select>
      </v-col>
    </v-row>
    <v-row>
      <v-expansion-panels>
        <v-expansion-panel>
          <v-expansion-panel-title>
            <v-icon> mdi-cart-variant</v-icon>
            <v-spacer></v-spacer>
            신규 상품을 등록하려면 클릭해주세요.
          </v-expansion-panel-title>
          <v-expansion-panel-text>
            <v-container>
              <v-row>
                <v-col cols="8">
                  <v-text-field label="상품명" v-model="name" placeholder="상품 이름을 적으세요." clearable></v-text-field>
                </v-col>
                <v-col cols="4">
                  <v-text-field label="가격" v-model.number="price" placeholder="가격은 숫자로만 적으세요." clearable></v-text-field>
                </v-col>
              </v-row>
              <v-row>
                <v-col align="center">
                  <v-btn @click="addItem" variant="outlined" prepend-icon="mdi-cart-variant" color="primary">상품 추가</v-btn>
                </v-col>
              </v-row>
            </v-container>
          </v-expansion-panel-text>
        </v-expansion-panel>
      </v-expansion-panels>
    </v-row>

    <v-row>
      <v-col class="d-flex justify-center">
        <v-sheet elevation="5" height="2rem" width="300" color="primary" align="center">총 지불금액: {{ totalPrice.toLocaleString() }}</v-sheet>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" class="d-flex flex-wrap">
        <v-card v-for="item in filteredList" :key="item.id" :title="item.name" :subtitle="item.price + '원'" width="230" height="180" variant="outlined"></v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
/* eslint-disable */
import { ref, computed } from "vue";
let id = 0;
const name = ref();
const price = ref(0);
const list = ref([
  { id: id++, name: "새우깡", price: 1600 },
  { id: id++, name: "초코파이", price: 1700 },
  { id: id++, name: "에이스", price: 1230 },
  { id: id++, name: "양파링", price: 2300 },
]);

const calTotalPrice = function () {
  return list.value.reduce((acc, cur) => acc + cur.price, 0);
};

const totalPrice = computed(calTotalPrice);

const addItem = function () {
  const newItem = {
    id: id++,
    name: name.value,
    price: price.value,
  };
  list.value.push(newItem);
  name.value = "";
  price.value = 0;
};

const filterPrice = ref({ label: "정렬 안함", price: 0 });
const priceItem = [
  { label: "정렬 안함", price: 0 },
  { label: "1500원", price: 1500 },
  { label: "3000원", price: 3000 },
];

const sortProp = ref({ title: "정렬 안함", method: "" });
const sortItem = [
  { title: "정렬 안함", method: "" },
  { title: "오름차순", method: "asc" },
  { title: "내림차순", method: "desc" },
];

const filteredList = computed(() => {
  let newlist = list.value.filter((item) => item.price >= filterPrice.value.price);
  if (sortProp.value !== "") {
    newlist = newlist.sort((a, b) => (sortProp.value === "asc" ? a.price - b.price : b.price - a.price));
  }
  return newlist;
});
</script>
