<script setup>
import { computed } from "vue";

const props = defineProps(["productOne", "productTwo"]);

const cheapest = computed(() => {
  if (props.productOne.price < props.productTwo.price)
    return props.productOne.title;
  else return props.productTwo.title;
});
const mostExpensive = computed(() => {
  if (props.productOne.price > props.productTwo.price)
    return props.productOne.title;
  else return props.productTwo.title;
});
const x = computed(() => {
  if (props.productOne.price < props.productTwo.price)
    return Math.round(props.productTwo.price / props.productOne.price);
  else return Math.round(props.productOne.price / props.productTwo.price);
});
</script>

<template>
  <p class="mx-5 text-center" v-if="props.productOne && props.productTwo">
    You can get <strong>{{ x }}</strong> <em> {{ cheapest }}</em> for about the
    same price as a single
    <em> {{ mostExpensive }}</em>
  </p>
</template>
