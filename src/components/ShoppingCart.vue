<template>
  <h1>Shopping Cart</h1>
  <ul>
    <li v-for="item in cart" :key="item.id" class="cart-item">
      <span
        >{{ item.product.name }} - ${{ item.product.price }} - Quantity:
        {{ item.quantity }}</span
      >
      <button @click="removeFromCart(item)">Remove</button>
      <button @click="updateQuantity(item, 'increment')">+</button>
      <button @click="updateQuantity(item, 'decrement')">-</button>
    </li>
  </ul>

  <p id="total">
    Total: <span style="font-weight: bold">${{ total }}</span>
  </p>
</template>

<script>
export default {
  props: ["cart"],
  methods: {
    removeFromCart(item) {
      const index = this.cart.indexOf(item);
      if (index !== -1) {
        // eslint-disable-next-line vue/no-mutating-props
        this.cart.splice(index, 1);
      }
    },
    updateQuantity(item, action) {
      if (action === "increment") {
        item.quantity++;
      } else if (action === "decrement") {
        if (item.quantity > 1) {
          item.quantity--;
        }
      }
    },
  },
  computed: {
    total() {
      return this.cart.reduce(
        (acc, item) => acc + item.product.price * item.quantity,
        0
      );
    },
  },
};
</script>

<style scoped>
#total {
  font-weight: bold;
}

.cart-item {
  display: flex;
  align-items: center; 
  padding: 10px;
  border-bottom: 1px solid #645a5a;
}

.cart-item span {
  flex-grow: 1; 
  padding: 5px;
}

.cart-item button {
  padding: 8px 15px; 
  margin-left: 5px; 
}

.total-amount {
  font-weight: bold;
  font-size: 20px;
}
</style>
