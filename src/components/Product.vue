<template>
  <img class="img" :src="product?.image" alt="Image" />
  <div class="product-wrapper">
    <div class="title-wrapper">
      <h1
        :class="
          product?.category === `men's clothing` ? `text-men` : `text-women`
        "
      >
        {{ product?.title }}
      </h1>
    </div>
    <div class="category-wrapper">
      <p>{{ product?.category }}</p>
      <div class="rating-wrapper">
        <p>{{ product?.rating?.rate }}</p>
        <div class="rating">
          <span
            v-for="i in 5"
            v-if="product?.category === `men's clothing`"
            :class="[
              product?.rating?.rate >= i ? 'fill-rate-men' : 'unfill-rate-men',
            ]"
          ></span>
          <span
            v-for="i in 5"
            v-if="product?.category === `women's clothing`"
            :class="[
              product?.rating?.rate >= i
                ? 'fill-rate-women'
                : 'unfill-rate-women',
            ]"
          ></span>
        </div>
      </div>
    </div>
    <div class="description-wrapper" :title="product?.description">
      <div class="inner-description-wrapper">
        <p>
          {{ product?.description }}
        </p>
      </div>
    </div>
    <div class="price-wrapper">
      <p
        :class="
          product?.category === `men's clothing` ? `text-men` : `text-women`
        "
      >
        $ {{ product?.rating?.count }}
      </p>
    </div>
    <div class="button-wrapper">
      <button
        :class="
          product?.category === `men's clothing` ? `btn-men` : `btn-women`
        "
      >
        Buy now
      </button>
      <button
        @click="handleClick"
        :class="
          product?.category === `men's clothing` ? `btn-men` : `btn-women`
        "
      >
        Next Product
      </button>
    </div>
  </div>
</template>

<script setup>
defineProps({
  product: Object,
  isLoading: Boolean,
});

const emit = defineEmits(['click']);

const handleClick = () => {
  emit('click');
};
</script>
