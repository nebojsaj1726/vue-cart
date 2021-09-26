<template>
  <div>
    <h1>Your Cart</h1>
    <CartItemCard v-for="item in items" :key="item.id" :product="item" />
    <CartSummaryCard />
  </div>
</template>

<script>
import CartItemCard from "../components/cart/CartItemCard.vue";
import CartSummaryCard from "../components/cart/CartSummaryCard.vue";

export default {
  components: {
    CartItemCard,
    CartSummaryCard,
  },
  computed: {
    items() {
      return this.$store.getters.cartItems;
    },
  },
};
</script>
