<template>
  <div class="bg-sad"></div>
  <div class="wrapper-unavailable">
    <p>This product is unavailable to show</p>
    <button
      @click="handleClick"
      :class="
        (product?.category !== `women's clothing` ||
          product?.category !== `men's clothing`) &&
        `btn-unavailable`
      "
    >
      Next Product
    </button>
  </div>
</template>

<script setup>
defineProps({
  product: Object,
});

const emit = defineEmits(['click']);

const handleClick = () => {
  emit('click');
};
</script>
