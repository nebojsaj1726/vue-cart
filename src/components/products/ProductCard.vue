<template>
  <div class="card">
    <h3>{{ product.name }}</h3>
    <h4 class="price">Price: ${{ product.price.toFixed(2) }}</h4>
    <p class="description">Description: {{ product.description }}</p>
    <p class="text-muted">{{ product.category }}</p>
    <button class="button" @click="$emit('view-product', product)">
      View
    </button>
  </div>
</template>

<script>
export default {
  props: ["product"],
};
</script>

<style lang="scss" scoped>
.card {
  margin: 20px;
  padding: 10px 20px;
  background-color: whitesmoke;
  box-shadow: 0 0 2px gray;

  .description {
    font-size: 0.85rem;
  }

  .text-muted {
    color: gray;
  }
}
</style>
