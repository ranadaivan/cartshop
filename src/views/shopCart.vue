<template>
  <div class="content">
    <div class="item-list">
      <h3 class="section-title">Item List</h3>
      <table class="item-table">
        <tr>
          <th>Item</th>
          <th>Price</th>
          <th></th>
        </tr>
        <itemList itemName="Pizza" :itemPrice="12" @addCart="addToArray" />
        <itemList itemName="Burger" :itemPrice="8" @addCart="addToArray" />
        <itemList itemName="Salad" :itemPrice="10" @addCart="addToArray" />
        <itemList itemName="Ice Cream" :itemPrice="5" @addCart="addToArray" />
      </table>
    </div>
    <div class="cart-list">
      <h3 class="section-title">Shopping Cart</h3>
      <cartList :cartList="cartList" @removeCart="removeToArray" />
    </div>
  </div>
</template>

<script>
import itemList from '@/components/itemList.vue'
import cartList from '@/components/cartList.vue'

export default {
  name: 'ShopApp',
  components: {
    itemList,
    cartList
  },

  data() {
    return {
      cartList: []
    }
  },

  methods: {
    addToArray(item) {
      this.cartList.push(item);
      console.log('Cart List:', this.cartList);
    },

    removeToArray(index) {
      this.cartList.splice(index, 1);
    },
  }
}
</script>

<style>

.content {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 20px;
}

.item-list, .cart-list {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
}

.section-title {
  font-size: 24px;
  margin-bottom: 15px;
}

.item-table {
  width: 100%;
  border-collapse: collapse;
}

.item-table th, .item-table td {
  padding: 10px;
  text-align: center;
  border-bottom: 1px solid #ddd;
}

.item-table th {
  background-color: #007bff;
  color: #fff;
}

.cart-list {
  background-color: #e9e9e9;
}

.cart-list {
  background-color: #f9f9f9;
  padding: 20px;
  border-radius: 8px;
}
</style>