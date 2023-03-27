<template>
  <main>
    <div class="container">
      <div class="products">
        <div class="texts">
          <div>
            <h1>buy yo groceries here</h1>
          </div>
        </div>

        <div class="cards">
          <Card
            v-for="products in products"
            :key="products.title"
            :title="products.title"
            :description="products.description"
            :image="products.image"
          />
        </div>
        
      </div>
      <div class="shoppingList">
          <img class="shoppingPaper" src="../src/assets/shoppingList.png" alt="" />
      </div>
    </div>
  </main>
</template>

<script>
import Button from "./components/Button.vue";
import Card from "./components/Card.vue";
import { products } from "../src/assets/products";

export default {
  data() {
    return {
      products,
    };
  },

  components: {
    Button,
    Card,
  },
};
</script>

<style>
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
  .shoppingPaper {
    width: 20vw;
  }
</style>
