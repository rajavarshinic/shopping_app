<template>
    <div class="checkout">
      <h2>🧾 Checkout</h2>
      <form @submit.prevent="submitOrder">
        <input v-model="name" type="text" placeholder="Full Name" required />
        <input v-model="address" type="text" placeholder="Address" required />
        <button type="submit">Place Order</button>
      </form>
      <p v-if="submitted">✅ Order placed! Thank you, {{ name }}.</p>
    </div>
  </template>
  
  <script>
  export default {
    name: "CheckoutForm",
    data() {
      return {
        name: "",
        address: "",
        submitted: false,
      };
    },
    methods: {
      submitOrder() {
        if (this.name && this.address) {
          this.submitted = true;
          this.$emit("order-placed");
        }
      },
    },
  };
  </script>
  
  <style>
  .checkout {
    margin-top: 40px;
  }
  .checkout input {
    display: block;
    margin: 10px auto;
    padding: 10px;
    width: 60%;
    max-width: 300px;
  }
  .checkout button {
    background-color: #42b983;
    color: white;
    border: none;
    padding: 10px 20px;
    cursor: pointer;
  }
  </style>
  