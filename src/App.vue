<template>
  <div id="app">
    <header>
      <h1>🛒 My Shopping App</h1>
      <p class="cart-count">🧺 Items in Cart: {{ cart.length }}</p>
    </header>
    <main>
      <p>Welcome to the store. Start shopping!</p>
      <ProductList @add-to-cart="addToCart" />

      <div class="cart">
        <h2>🧺 Cart</h2>
        <ul>
          <li v-for="(item, index) in cart" :key="index">
            {{ item.name }} - ₹{{ item.price }}
            <button @click="removeFromCart(index)">Remove</button>
          </li>
        </ul>
        <p v-if="cart.length === 0">Your cart is empty.</p>
        <p v-else><strong>Total:</strong> ₹{{ totalPrice }}</p>
      </div>

      <CheckoutForm @order-placed="clearCart" />
    </main>
  </div>
</template>

<script>
import ProductList from "./components/ProductList.vue";
import CheckoutForm from "./components/CheckoutForm.vue";

export default {
  name: "App",
  components: {
    ProductList,
    CheckoutForm,
  },
  data() {
    return {
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      this.cart.push(product);
    },
    removeFromCart(index) {
      this.cart.splice(index, 1);
    },
    clearCart() {
      this.cart = [];
    },
  },
  computed: {
    totalPrice() {
      return this.cart.reduce((sum, item) => sum + item.price, 0);
    },
  },
};
</script>

<style>
#app {
  text-align: center;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  margin-top: 60px;
}
header {
  background-color: #42b983;
  padding: 20px;
  color: white;
}
.cart-count {
  font-size: 18px;
  margin-top: 10px;
}
.cart {
  margin-top: 40px;
  padding: 20px;
  border-top: 1px solid #ccc;
}
.cart ul {
  list-style: none;
  padding: 0;
}
.cart li {
  margin: 10px 0;
}
.cart button {
  margin-left: 10px;
  background-color: crimson;
  color: white;
  border: none;
  padding: 5px;
  cursor: pointer;
}
</style>
