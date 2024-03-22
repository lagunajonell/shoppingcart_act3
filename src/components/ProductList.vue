<template>
  <h1>Products</h1>
  <ul>
    <li v-for="product in products" :key="product.id" class="product-item">
      <img
        :src="product.imageUrl"
        alt="Product Image"
        style="width: 100px; height: 100px"
      />
      <span>{{ product.name }} - ${{ product.price }}</span>
      <button @click="addToCart(product)">Add to Cart</button>
    </li>
  </ul>

  <ShoppingCart :cart="cart" />
</template>

<script>
import ShoppingCart from "./ShoppingCart.vue";
import chippy from "../assets/chippy.jpg";
import vcut from "../assets/vcut.jpg";
import piattos from "../assets/piattos.jpg";
import dingdong from "../assets/dingdong.jpg";
import cracklings from "../assets/cracklings.jpg";
import oishi from "../assets/oishi.jpg";
import clover from "../assets/clover.jpg";
import pillow from "../assets/pillow.jpg";
import rollercoaster from "../assets/rollercoaster.jpg";
import peewee from "../assets/peewee.jpg";


export default {
  name: "App",
  components: {
    ShoppingCart,
  },
  data() {
    return {
      products: [
        { id: 1, name: "Chippy", price: 10, imageUrl: chippy },
        { id: 2, name: "V-Cut", price: 15, imageUrl: vcut },
        { id: 3, name: "Piattos", price: 15, imageUrl: piattos },
        { id: 4, name: "Ding-Dong", price: 7, imageUrl: dingdong },
        { id: 5, name: "Cracklings", price: 7, imageUrl: cracklings },
        { id: 6, name: "Oishi", price: 8, imageUrl: oishi },
        { id: 7, name: "Clover", price: 8, imageUrl: clover },
        { id: 8, name: "Pillow", price: 15, imageUrl: pillow },
        {
          id: 9,
          name: "Roller Coaster",
          price: 7,
          imageUrl: rollercoaster,
        },
        { id: 10, name: "PeeWee", price: 7, imageUrl: peewee },
      ],
      cart: [],
    };
  },
  methods: {
    addToCart(product) {
      let cartItem = this.cart.find((item) => item.product.id === product.id);
      if (cartItem) {
        cartItem.quantity++;
      } else {
        this.cart.push({ product: product, quantity: 1 });
      }
    },
  },
};
</script>

<style scoped>
body {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
  margin: 0;
}

#app {
  text-align: center;
  max-width: 600px;
  margin: 0 auto;
}

.product-list {
  display: flex;
  flex-wrap: wrap;
  justify-content: center; 
}

.product-item {
  width: 100%; 
  margin-bottom: 10px; 
}

ul {
  list-style-type: none;
  padding: 0;
  text-align: left;
  counter-reset: list-counter;
}

ul li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  counter-increment: list-counter;
  margin-bottom: 2px; 
}

ul li::before {
  content: counter(list-counter) ". ";
  margin-right: 5px;
}

.product-number {
  display: none; 
}

.product-image {
  width: 50px; 
  height: auto; 
  margin-right: 10px; 
}

.product-name {
  flex: 1; 
}

button {
  background-color: #13b8eb;
  color: rgb(0, 0, 0);
  padding: 8px 15px; 
  border: none;
  cursor: pointer;
  margin-left: 5px; 
}
</style>



