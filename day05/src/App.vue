<script setup lang="ts">
import { ref } from 'vue'

import GiftLabel from './components/GiftLabel.vue'

const from = ref('')
const to = ref('')
</script>

<template>
  <div class="w-full h-full flex justify-center items-center">
    <div>
      <GiftLabel :from="from" :to="to" />
      <div class="mt-6">
        <label class="block">
          To:
          <input
            v-model="to"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2"
          />
        </label>
        <label class="mt-2 block">
          From:
          <input
            v-model="from"
            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2"
          />
        </label>
      </div>
    </div>
  </div>
</template>
