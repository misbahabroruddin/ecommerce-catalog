<template>
  <Background :product="product" />
  <div class="container">
    <Loading :is-loading="isLoading" />
    <div
      class="inner-container"
      v-if="
        (product?.category === `women's clothing` ||
          product?.category === `men's clothing`) &&
        !isLoading
      "
    >
      <Product :product="product" @click="incrementId" />
    </div>
    <div
      class="inner-container"
      v-else-if="
        (product?.category !== `women's clothing` ||
          product?.category !== `men's clothing`) &&
        !isLoading
      "
    >
      <ProductUnavailable :product="product" @click="incrementId" />
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref, watch } from 'vue';
import Background from './components/Background.vue';
import ProductUnavailable from './components/ProductUnavailable.vue';
import Loading from './components/Loading.vue';
import Product from './components/Product.vue';

const Id = ref(1);
const isLoading = ref(false);
const product = ref({});

const fetchProduct = async () => {
  try {
    isLoading.value = true;
    const res = await fetch(`https://fakestoreapi.com/products/${Id.value}`);
    const data = await res.json();
    product.value = data;
    isLoading.value = false;
  } catch (error) {
    alert(error.message);
  }
};

onMounted(async () => {
  await fetchProduct();
});

const incrementId = () => {
  Id.value++;
  if (Id.value > 20) {
    Id.value = 1;
  }
};

watch(Id, async () => {
  await fetchProduct();
});
</script>
