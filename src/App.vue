<template>
  <div id="nav">
    <router-link :class="{ active: $route.name === 'Home' }" to="/"
      >Home</router-link
    >
    <router-link :class="{ active: $route.name === 'Cart' }" to="/cart"
      >Cart</router-link
    >
  </div>
  <router-view />
</template>

<script>
export default {
  mounted() {
    this.$store.commit("updateCartFromLocalStorage");
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

* {
  box-sizing: border-box;
}

#nav {
  padding: 10px;
  width: 100%;

  a {
    font-weight: bold;
    color: darkgray;
    text-decoration: none;
    margin: 0 5px;

    &.active {
      color: #2c3e50;
    }
  }
}

.text-center {
  text-align: center;
}

.button {
  padding: 10px;
  background-color: green;
  border: none;
  color: #fff;
  font-weight: bold;
  border-radius: 5px;
  cursor: pointer;
}
</style>
