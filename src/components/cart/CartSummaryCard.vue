<template>
  <div class="cart-item-card">
    <h2>Cart Total: ${{ cart_total.toFixed(2) }}</h2>
    <button class="button">
      Pay by Credit Card
    </button>
  </div>
</template>

<script>
export default {
  computed: {
    cart_total() {
      return this.$store.getters.cartTotal;
    },
  },
};
</script>
