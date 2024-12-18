<!-- src/components/Bookstore.vue -->

<template>
    <div class="bookstore-container">
      <h1>Книжный магазин</h1>
      <p>Это компонент книжного магазина.</p>
      <ul class="book-list">
        <li v-for="book in books" :key="book.id">
          <h2>{{ book.title }}</h2>
          <p>Автор: {{ book.author }}</p>
          <p>Цена: {{ book.price }} руб.</p>
          <button @click="addToCart(book)">Добавить в корзину</button>
        </li>
      </ul>
      <div class="cart-container">
        <h2>Корзина</h2>
        <ul class="cart-list">
          <li v-for="item in cart" :key="item.id">
            <h2>{{ item.title }}</h2>
            <p>Количество: {{ item.quantity }}</p>
            <p>Цена: {{ item.price }} руб.</p>
            <button @click="removeFromCart(item)">Удалить из корзины</button>
          </li>
        </ul>
        <p>Общая сумма: {{ totalSum }} руб.</p>
      </div>
    </div>
  </template>
  
  <script>
  export default {
    name: 'BookstoreComponent',
    data() {
      return {
        books: [
          { id: 1, title: 'Книга 1', author: 'Автор 1', price: 100 },
          { id: 2, title: 'Книга 2', author: 'Автор 2', price: 200 },
          { id: 3, title: 'Книга 3', author: 'Автор 3', price: 300 },
        ],
        cart: [],
      }
    },
    methods: {
      addToCart(book) {
        const existingItem = this.cart.find(item => item.id === book.id);
        if (existingItem) {
          existingItem.quantity++;
        } else {
          this.cart.push({ ...book, quantity: 1 });
        }
        this.calculateTotalSum();
      },
      removeFromCart(item) {
        this.cart = this.cart.filter(cartItem => cartItem.id !== item.id);
        this.calculateTotalSum();
      },
      calculateTotalSum() {
        const totalSum = this.cart.reduce((acc, item) => acc + item.price * item.quantity, 0);
        this.totalSum = totalSum;
      }
    }
  };
  </script>
  
  <style scoped>
  .bookstore-container {
    max-width: 800px;
    margin: 40px auto;
    padding: 20px;
    background-color: #f7f7f7;
    border: 1px solid #ddd;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
  
  .book-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .book-list li {
    margin-bottom: 20px;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .book-list li:last-child {
    border-bottom: none;
  }
  
  .cart-container {
    margin-top: 40px;
  }
  
  .cart-list {
    list-style: none;
    padding: 0;
    margin: 0;
  }
  
  .cart-list li {
    margin-bottom: 20px;
    padding: 10px;
    border-bottom: 1px solid #ccc;
  }
  
  .cart-list li:last-child {
    border-bottom: none;
  }
  </style>
  
  
  