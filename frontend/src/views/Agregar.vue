<template>
    <div>
      <h2>Shopping Cart</h2>
      <div v-if="products.length === 0">
        <p>No products in the cart.</p>
      </div>
      <ul v-else>
        <li v-for="(product, index) in products" :key="product.id">
          {{ product.name }} - ${{ product.price }} - Quantity:
          <input type="number" v-model.number="product.quantity" min="1" @input="calculateTotal(product)">
          Total: ${{ product.totalPrice }}
          <button @click="removeProduct(index)">Remove</button>
        </li>
        <p><strong>Overall Total: ${{ overallTotal }}</strong></p>
      </ul>
      <div>
        <h3>Available Products</h3>
        <ul>
          <li v-for="product in availableProducts" :key="product.id">
            {{ product.name }} - ${{ product.price }}
            <input type="number" v-model.number="product.quantityToAdd" min="1">
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
          { id: 1, name: 'Inka Kola', price: 2.50, quantityToAdd: 1 },
          { id: 2, name: 'Coca Cola', price: 2.50, quantityToAdd: 1 },
          { id: 3, name: 'Fanta', price: 2.0, quantityToAdd: 1 },
          { id: 3, name: 'Sprite', price: 2.0, quantityToAdd: 1 },
        ],
      };
    },
    computed: {
      overallTotal() {
        return this.products.reduce((total, product) => total + product.totalPrice, 0);
      },
    },
    methods: {
      addProduct(product) {
        const { id, name, price, quantityToAdd } = product;
        const existingProduct = this.products.find(p => p.id === id);
  
        const quantity = parseInt(quantityToAdd);
        if (!quantity || quantity <= 0) {
          alert('Please enter a valid quantity.');
          return;
        }
  
        if (existingProduct) {
          existingProduct.quantity += quantity;
          existingProduct.totalPrice = existingProduct.price * existingProduct.quantity;
        } else {
          const newProduct = {
            id,
            name,
            price,
            quantity,
            totalPrice: price * quantity,
          };
          this.products.push(newProduct);
        }
      },
      removeProduct(index) {
        this.products.splice(index, 1);
      },
      calculateTotal(product) {
        product.totalPrice = product.price * product.quantity;
      },
    },
  };
  </script>
  