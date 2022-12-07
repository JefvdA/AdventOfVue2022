<script setup lang="ts">
import { ref, watch } from "vue";

import ItemSelect from "./components/ItemSelect.vue";
import ComparisonSummary from "./components/ComparisonSummary.vue";

const productOne = ref();
const productTwo = ref();

function onProductOneChange(newProduct) {
  productOne.value = newProduct;
}

function onProductTwoChange(newProduct) {
  productTwo.value = newProduct;
}
</script>

<template>
  <div class="w-full h-full flex flex-col gap-5 justify-center items-center">
    <h1 class="text-4xl font-bold">Select items to compare</h1>
    <div class="flex flex-col gap-5 justify-center">
      <ItemSelect @on-value-change="onProductOneChange" />
      <ItemSelect @on-value-change="onProductTwoChange" />
    </div>
    <ComparisonSummary :product-one="productOne" :product-two="productTwo"/>
  </div>
</template>
