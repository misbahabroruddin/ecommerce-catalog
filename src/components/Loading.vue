<template>
  <div class="inner-container" v-if="isLoading">
    <div class="skeleton skeleton-img"></div>
    <div class="product-wrapper">
      <div class="title-wrapper">
        <div class="skeleton skeleton-text-full"></div>
      </div>
      <div class="category-wrapper">
        <div class="skeleton skeleton-text-200"></div>

        <div class="rating-wrapper">
          <div class="skeleton skeleton-text-200"></div>
        </div>
      </div>
      <div class="description-wrapper">
        <div class="skeleton skeleton-text-full"></div>
        <div
          class="skeleton skeleton-text-full"
          style="margin-top: 0.5rem"
        ></div>
        <div
          class="skeleton skeleton-text-full"
          style="margin-top: 0.5rem"
        ></div>
      </div>
      <div class="price-wrapper">
        <div class="skeleton skeleton-text-200"></div>
      </div>
      <div class="button-wrapper">
        <div class="skeleton skeleton-text-full"></div>
        <div class="skeleton skeleton-text-full"></div>
      </div>
    </div>
  </div>
</template>

<script setup>
defineProps({
  isLoading: Boolean,
});
</script>

<style scoped>
.skeleton {
  animation: skeleton-loading 1s linear infinite alternate;
}

.skeleton-img {
  width: 350px;
  height: 450px;
  border-radius: 5px;
}

.skeleton-text-full {
  width: 100%;
  height: 1.7rem;
  border-radius: 5px;
}

.skeleton-text-200 {
  width: 200px;
  height: 1.7rem;
  border-radius: 5px;
}

@keyframes skeleton-loading {
  0% {
    background-color: hsl(200, 20%, 80%);
  }
  100% {
    background-color: hsl(200, 20%, 95%);
  }
}
</style>
