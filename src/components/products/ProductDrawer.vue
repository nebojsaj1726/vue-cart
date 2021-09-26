<template>
  <div
    class="drawer-background"
    :class="{ show: active }"
    @click="$emit('close-product-drawer')"
  />

  <div class="drawer" :class="{ show: active }">
    <div class="drawer-close" @click="$emit('close-product-drawer')">X</div>

    <div class="product-details" v-if="product">
      <h3 class="text-center">{{ product.name }}</h3>
      <p class="description">{{ product.description }}</p>
      <h3 class="text-center">${{ product.price }}</h3>

      <div class="cart-total" v-if="product_total">
        <h3>In Cart</h3>
        <h4>{{ product_total }}</h4>
      </div>

      <div class="button-container">
        <button class="remove" @click="removeFromCart()">Remove</button>
        <button class="add" @click="addToCart()">Add</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["product", "active"],
  emits: ["close-product-drawer"],
  methods: {
    addToCart() {
      this.$store.commit("addToCart", this.product);
    },
    removeFromCart() {
      this.$store.commit("removeFromCart", this.product);
    },
  },
  computed: {
    product_total() {
      return this.$store.getters.productQuantity(this.product);
    },
  },
};
</script>

<style lang="scss" scoped>
.drawer-background {
  width: 100%;
  height: 100vh;
  position: fixed;
  left: 0;
  top: 0;
  background-color: rgba(124, 124, 124, 0.55);
  z-index: 1;
  display: none;

  &.show {
    display: block;
  }
}

.drawer {
  width: 70%;
  height: 100vh;
  background-color: #fff;
  position: fixed;
  top: 0;
  left: -105vw;
  transition: left 0.5s;
  z-index: 2;

  @media (max-width: 560px) {
    width: 90%;
  }

  &.show {
    left: 0;
  }

  .drawer-close {
    padding: 5px;
    border: 2px solid gray;
    margin-right: 10px;
    margin-top: 10px;
    border-radius: 5px;
    color: gray;
    width: 33px;
    float: right;
    cursor: pointer;

    &:hover {
      background-color: lightgray;
    }
  }

  .product-details {
    display: flex;
    justify-content: center;
    flex-direction: column;

    .description {
      padding: 20px;
    }

    .button-container {
      button {
        width: 150px;
        border: none;
        padding: 10px;
        border-radius: 5px;
        margin: 0 5px 50px 5px;
        background-color: green;
        cursor: pointer;
        color: #fff;

        @media (max-width: 560px) {
          width: 100px;
        }
      }
    }
  }
}
</style>
