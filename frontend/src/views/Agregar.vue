<template>
    <div class="shopping-cart">
      <h2>Shopping Cart</h2>
      <div v-if="products.length === 0">
        <p>No hay productos en el carro.</p>
      </div>
      <ul v-else>
        <li v-for="(product, index) in products" :key="product.id" class="cart-item">
          <div class="product-info">
            <div class="product-image">
              <img :src="product.image" :alt="product.name">
            </div>
            <div class="product-details">
              <span class="product-name">{{ product.name }}</span>
              <span class="product-price">S/.{{ product.price }}</span>
            </div>
          </div>
          <div class="quantity">
            Quantity:
            <input type="number" v-model.number="product.quantity" min="1" @input="calculateTotal(product)">
          </div>
          <div class="total-price">
            Total: S/.{{ product.totalPrice }}
          </div>
          <button class="remove-btn" @click="removeProduct(index)">Remove</button>
        </li>
        <p class="overall-total"><strong>Total: S/.{{ overallTotal }}</strong></p>
        <button class="buy-btn" @click="buyProducts">Buy</button>
      </ul>
      <div>
        <h3>Productos disponibles</h3>
        <ul>
          <li v-for="product in availableProducts" :key="product.id" class="product-item">
            <div class="product-info">
            <div class="product-image">
              <img :src="product.image" :alt="product.name">
            </div>
            <div class="product-details">
              <span class="product-name">{{ product.name }}</span>
              <span class="product-price">S/.{{ product.price }}</span>
            </div>
          </div>
            <div class="quantity">
               Cantidad:
              <input type="number" v-model.number="product.quantityToAdd" min="1">
            </div>
            <button class="add-btn" @click="addProduct(product)">Añadir al carrito</button>
          </li>
        </ul>
      </div>
      <div v-if="showSuccessMessage" class="success-message">
        <p>Compra exitosa</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        products: [],
        availableProducts: [
          { id: 1, name: 'Coca Cola ', price: 2.5, quantityToAdd: 1, image: '/assets/sprite.jpg' },
          { id: 2, name: 'Pepsi ', price: 2.5, quantityToAdd: 1 },
          { id: 3, name: 'Fanta ', price: 2.0, quantityToAdd: 1 },
          { id: 3, name: 'Sprite ', price: 2.0, quantityToAdd: 1 },
          { id: 3, name: 'Seven Up ', price: 1.5, quantityToAdd: 1 },
        ],
        showSuccessMessage: false,
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
          alert('Por favor, ingres una cantidad valida.');
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
      buyProducts() {
        if (this.products.length === 0) {
          alert('Please add products to the cart before buying.');
          return;
        }
  
        // API request, UPDATE DB
        this.showSuccessMessage = true;
        this.products = [];
      },
    },
  };
  </script>
  
  <style>
  .shopping-cart {
    max-width: 500px;
    margin: 0 auto;
    padding: 20px;
    background-color: #f8f8f8;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
  
  h2 {
    text-align: center;
    margin-bottom: 20px;
  }
  
  .cart-item {
    list-style: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 10px;
    padding: 10px;
    background-color: #fff;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
  
  .product-item {
    list-style: none;
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 10px;
    padding: 10px;
    background-color: #f8f8f8;
    border: 1px solid #ddd;
    border-radius: 5px;
  }

  .product-details {
  display: flex;
  flex-direction: column;
}

.product-name {
  font-weight: bold;
  margin-bottom: 5px;
}

.product-price {
  color: #777;
}

.product-image {
  width: 100px;
  height: 100px;
  margin-right: 10px;
}

.product-image img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 5px;
}

  
  .product-info {
    display: flex;
    align-items: center;
  }

  .quantity {
    flex: 1;
    display: flex;
    align-items: center;
  }
  
  .total-price {
    flex: 1;
    text-align: right;
  }
  
  .remove-btn,
  .add-btn,
  .buy-btn {
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 3px;
    padding: 5px 10px;
    cursor: pointer;
  }
  
  .remove-btn {
    background-color: #dc3545;
    margin-left: 10px;
  }
  
  .buy-btn {
    margin-top: 20px;
    width: 100%;
  }
  
  .success-message {
    margin-top: 20px;
    text-align: center;
    padding: 10px;
    background-color: #dff0d8;
    color: #3c763d;
    border: 1px solid #d6e9c6;
    border-radius: 5px;
  }
  </style>
  