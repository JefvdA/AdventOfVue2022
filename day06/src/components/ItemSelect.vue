<script setup>
import { ref, watch } from "vue";

const selected = ref();
const products = ref([]);

const emit = defineEmits(["onValueChange"]);

function fetchProducts() {
  fetch("https://dummyjson.com/products")
    .then((res) => res.json())
    .then((data) => {
      products.value = data.products;
    });
}

fetchProducts();

watch(selected, async (newSelected, oldSelected) => {
  emit("onValueChange", newSelected);
});
</script>

<template>
  <select v-model="selected" class="p-2 border-2 border-gray-dark">
    <option :value="product" v-for="product in products">
      {{ product.title }}
    </option>
  </select>
</template>
