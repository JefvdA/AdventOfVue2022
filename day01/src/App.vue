<script setup>
import { ref, watch } from 'vue'
import _ from 'lodash'

import LoadingSpinner from './components/LoadingSpinner.vue'

const loading = ref(false)
const searchTerm = ref('')
const products = ref([])

const findProducts = async term => {
  if (term == '') {
    products.value = []
    return
  }

  fetch('https://dummyjson.com/products/search?q=' + term)
    .then(res => res.json())
    .then(data => {
      products.value = data.products
      loading.value = false
    })
}

watch(products, () => {
  if (products.value.length == 0 && searchTerm.value != '') {
    alert("Sorry we couldn't find any products for " + searchTerm.value)
  }
})

watch(searchTerm, () => {
  loading.value = true
})

watch(searchTerm, _.debounce(findProducts, 300))
</script>

<template>
  <div class="w-full h-full flex flex-col gap-5 justify-center items-center">
    <h1 class="text-4xl font-bold">Gift Search Bar</h1>
    <input type="text" class="p-2 border-2 border-gray-dark" v-model="searchTerm" placeholder="Start typing..." />
    <LoadingSpinner v-if="loading" />
    <ul class="list-disc">
      <li v-for="product in products">{{ product.title }} - {{ product.price }}</li>
    </ul>
  </div>
</template>
