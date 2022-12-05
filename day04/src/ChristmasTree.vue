<template>
  <div>
    <div v-for="row in rows" class="flex flex-row justify-center">
      <!-- This div is styled for the tree sections, but it's not complete -->
      <div
        v-for="dot in row"
        :class="`${color()} relative rounded-full w-16 h-16 -m-2 flex justify-center items-center`"
      />
    </div>
  </div>
</template>

<script setup lang="ts">
import { defineProps, computed, ref } from 'vue'

const props = defineProps({
  size: Number,
})

const rows = computed(() => {
  let rows: number[] = []
  for (let i = 1; i <= props.size!; i++) {
    rows.push(i)
  }
  return rows
})

const color = () => {
  return Math.random() < 0.3 ? 'bg-red-500 z-10' : 'bg-green'
}
</script>
