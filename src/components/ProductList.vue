<template>
    <div class="product-list">
      <h2>🛍️ Products</h2>
      <ul>
        <li v-for="product in products" :key="product.id">
          <h3>{{ product.name }}</h3>
          <p>Price: ₹{{ product.price }}</p>
          <button @click="$emit('add-to-cart', product)">Add to Cart</button>
        </li>
      </ul>
    </div>
  </template>
  
  <script>
  export default {
    name: "ProductList",
    data() {
      return {
        products: [
          { id: 1, name: "T-shirt", price: 499 },
          { id: 2, name: "Jeans", price: 999 },
          { id: 3, name: "Sneakers", price: 1499 },
        ],
      };
    },
  };
  </script>
  
  <style>
  .product-list {
    margin-top: 40px;
    text-align: center;
  }
  .product-list ul {
    list-style: none;
    padding: 0;
  }
  .product-list li {
    border: 1px solid #ccc;
    margin: 15px;
    padding: 15px;
    border-radius: 8px;
  }
  button {
    background-color: #42b983;
    color: white;
    border: none;
    padding: 10px;
    cursor: pointer;
  }
  </style>
  