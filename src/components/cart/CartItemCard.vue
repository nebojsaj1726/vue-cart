<template>
  <div class="cart-item-card">
    <h2>{{ product.name }}</h2>
    <h4>{{ product.quantity }}</h4>
    <h4>Total Cost: {{ item_cost.toFixed(2) }}</h4>
  </div>
</template>

<script>
export default {
  props: ["product"],
  computed: {
    item_cost() {
      return this.product.price * this.product.quantity;
    },
  },
};
</script>

<style lang="scss">
.cart-item-card {
  width: 60%;
  margin: 20px auto;
  background-color: #fff;
  box-shadow: 0 0 2px gray;
  border-radius: 5px;
  padding: 10px;
  display: flex;
  justify-content: space-around;
  align-items: center;

  @media (max-width: 768px) {
    width: 90%;
  }
}
</style>
