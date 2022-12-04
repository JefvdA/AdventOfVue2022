<template>
  <div class="w-full h-full flex justify-center items-center">
    <span v-if="joke" class="text-3xl">{{ joke?.setup }}</span>
    <button
      v-if="joke && !revealed"
      @click="revealed = true"
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    >
      Tell me!
    </button>
    <span v-if="joke && revealed" class="text-3l">{{ joke?.delivery }}</span>
    <button
      v-if="joke && revealed"
      @click="fetchJoke(), (revealed = false)"
      class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
    >
      Another
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

interface Joke {
  setup: String
  delivery: String
}

const joke = ref<Joke | null>(null)
const revealed = ref(false)

async function fetchJoke() {
  const response = await fetch('https://v2.jokeapi.dev/joke/christmas')
  joke.value = await response.json()
}

fetchJoke()
</script>
