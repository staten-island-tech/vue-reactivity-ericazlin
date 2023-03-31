<template>
  <main>
    <div class="container">
      <div class="products">
        <div class="texts">
          <div>
            <h1>jeebee's gas station online pre-order</h1>
          </div>
        </div>

        <div class="cards">
          <Card
            v-for="product in products"
            :key="product.title"
            :title="product.title"
            :price="product.price"
            :image="product.image"
            @add-product="addToShoppingList"
          />
        </div>
      </div>
      <div class="shoppingList">

        <div class="prices">
          <p class="productAndPrice" v-for="product in shoppingList" :key="product.title">
          {{ product.title }} - ${{ product.price }}
          </p>
        </div> 

        <div class="total">
          <p class="total">Your total is ${{ total }}!</p>
        </div>

      </div>
    </div>
  </main>
</template>

<script>
import addButton from "./components/Button.vue";
import Card from "./components/Card.vue";
import { products } from "../src/assets/products";


export default {
  data() {
    return {
      products,
      shoppingList: [],
      total: 0,
    };
  },

  components: {
    addButton,
    Card,
  },

  methods: {
    addToShoppingList({ title, price }) {
      this.shoppingList.push({ title, price });
      this.total+=price;
    },
  },
};
</script>

<style>
html,
body {
  background-color: rgb(158, 182, 177);
}
.container {
  display: flex;
}
.products {
  width: 66vw;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}
.shoppingList {
  position: fixed;
  text-align: center;
  width: 34vw;
  left: 66vw;
}
</style>
