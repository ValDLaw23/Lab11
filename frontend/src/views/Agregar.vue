<template>
    <div>
      <h2>Shopping Cart</h2>
      <div v-if="products.length === 0">
        <p>No products in the cart.</p>
      </div>
      <ul v-else>
        <li v-for="(product, index) in products" :key="product.id">
          {{ product.name }} - ${{ product.price }}
          <button @click="removeProduct(index)">Remove</button>
        </li>
      </ul>
      <div>
        <h3>Available Products</h3>
        <ul>
          <li v-for="product in availableProducts" :key="product.id">
            {{ product.name }} - ${{ product.price }}
            <button @click="addProduct(product)">Add to Cart</button>
          </li>
        </ul>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        products: [],
        availableProducts: [
          { id: 1, name: 'Product 1', price: 10 },
          { id: 2, name: 'Product 2', price: 20 },
          { id: 3, name: 'Product 3', price: 30 },
        ],
      };
    },
    methods: {
      addProduct(product) {
        this.products.push(product);
      },
      removeProduct(index) {
        this.products.splice(index, 1);
      },
    },
  };
  </script>
  