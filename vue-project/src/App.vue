<template>
  <main>
    <div class="container">
      <div class="products">
        <div class="texts">
          <div>
            <h1>jeebee's gas station online pre-order</h1>
          </div>
        </div>

        <div class="filters">
          <button @click="filter(`exists`)">everything</button>
          <button @click="filter(`food`)">filter food</button>
          <button @click="filter(`frozen`)">filter frozen</button>
          <button @click="filter(`snack`)">filter snack</button>
          <button @click="filter(`fresh`)">filter fresh</button>
          <button @click="filter(`chemicals`)">filter chemicals</button>
          <button @click="filter(`hotFood`)">filter hot food</button>
          <button @click="filter(`carParts`)">filter car parts</button>
          <button @click="filter(`drinks`)">filter drinks</button>
          <button @click="filter(`coldFood`)">filter cold food</button>
          <button @click="filter(`candy`)">filter candy</button>
          <button @click="filter(`baked`)">filter baked</button>
        </div>

        <div class="cards">
          <Card
            v-for="product in filteredProducts"
            :key="product.title"
            :title="product.title"
            :price="product.price"
            :image="product.image"
            :amount="product.amount"
            @add-product="addToShoppingList"
          />
        </div>
      </div>
      <div class="shoppingList">

        <div class="prices">
          <p class="productAndPrice" v-for="product in shoppingList" :key="product.title">
            {{ product.title }} - ${{ product.price }} x {{ product.count }}
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
import addButton from "./components/addButton.vue";
import Card from "./components/Card.vue";
import { products } from "../src/assets/products";


export default {
  data() {
    return {
      products,
      filteredProducts: products,
      shoppingList: [],
      total: 0,
    };
  },

  components: {
    addButton,
    Card,
  },

  methods: {
    filter(productAttr) {
      this.filteredProducts = ((products.filter(product => product[productAttr] == true)))
    },

    addToShoppingList({ title, price }) {
      const existingProduct = this.shoppingList.find(product => product.title === title);

      if (existingProduct) {
        existingProduct.count++;
      } else {
        this.shoppingList.push({ title, price, count: 1 });
      }
      this.total += price;
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
