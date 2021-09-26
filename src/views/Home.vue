<template>
  <div class="home">
    <ProductDrawer
      :product="product"
      :active="active.product_drawer"
      v-on:close-product-drawer="closeProductDrawer()"
    />
    <div class="product-cards-container">
      <ProductCard
        v-for="item in items"
        :key="item.id"
        :product="item"
        v-on:view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
import items from "../data/items.js";
import ProductCard from "../components/products/ProductCard.vue";
import ProductDrawer from "../components/products/ProductDrawer.vue";

export default {
  name: "Home",
  components: {
    ProductCard,
    ProductDrawer,
  },
  data() {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false,
      },
    };
  },
  methods: {
    viewProduct(product) {
      this.product = product;
      this.active.product_drawer = true;
    },
    closeProductDrawer() {
      this.active.product_drawer = false;
    },
  },
};
</script>

<style lang="scss" scoped>
.home {
  padding: 40px 20px;
}

.product-cards-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
