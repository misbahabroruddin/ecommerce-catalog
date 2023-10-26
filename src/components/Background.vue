<template>
  <div
    v-if="product?.category === `men's clothing`"
    :class="product?.category === `men's clothing` && `bg-men`"
  ></div>
  <div
    v-else-if="product?.category === `women's clothing`"
    :class="product?.category === `women's clothing` && `bg-women`"
  ></div>
  <div
    v-else
    :class="
      (product?.category !== `women's clothing` ||
        product?.category !== `men's clothing`) &&
      `bg-unavailable`
    "
  ></div>

  <div></div>
</template>

<script setup>
defineProps({
  product: Object,
});
</script>
