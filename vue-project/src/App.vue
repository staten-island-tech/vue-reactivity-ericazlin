<template>
  <main>
    <div class="container container__whole">
      <div class="container container__products">
        <div class="text text__heading text__heading-title">
          <div>
            <h1>jeebee's gas station online pre-order</h1>
          </div>
        </div>

        <div class="container container__buttons">
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

        <div class="container container__cards">
          <Card
            v-for="product in filteredProducts"
            :key="product.title"
            :title="product.title"
            :price="product.price"
            :image="product.image"
            @addToCart="addToCart"
          />
        </div>
      </div>
      <div class="container container__cart">
        <div class="text text__heading text__heading-cart">
          <p>SHOPPING CART</p>
        </div>

        <div class="container container__prices">
          <p
            class="text text__items"
            v-for="product in shoppingList"
            :key="product.title"
          >
            {{ product.title }} - ${{ product.price }} x {{ product.quantity }}
          </p>
        </div>

        <div class="container container__total">
          <p class="text text__total">TOTAL: ${{ total }}</p>
        </div>

        <button @click="clearCart" class="button button__cart">
          Clear Cart
        </button>
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
      this.filteredProducts = products.filter(
        (product) => product[productAttr] == true
      );
    },

    addToCart({ title, price, quantity }) {
      const existingProduct = this.shoppingList.find(
        (product) => product.title === title
      );

      if (existingProduct) {
        existingProduct.quantity += quantity;
      } else {
        this.shoppingList.push({ title, price, quantity });
      }
      this.total += price * quantity;

      console.log(existingProduct);
    },
    clearCart() {
      this.shoppingList = [];
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
}

html,
body {
  background-color: rgb(158, 182, 177);
  font-family: "Trebuchet MS", "Lucida Sans Unicode", "Lucida Grande",
    "Lucida Sans", Arial, sans-serif;
}

.text__heading-title {
  font-size: 30px;
  margin: 5vh 0 2vh 0;
  margin-left: 1.4rem;
}

.text__heading-cart {
  font-size: 50px;
  margin-top: 5vh;
}

.button__cart {
  width: 10vw;
  height: 3vh;

  background-color: rgb(152, 211, 198);
  margin: 2vh 5vw;
}

.button__cart:active {
  background-color: rgb(158, 182, 177);
}

.container__whole {
  display: flex;
}

.container__products {
  width: 66vw;

  display: flex;
  flex-direction: column;
  align-items: center;
}

.container__buttons {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
}

.container__buttons button {
  width: 10vw;
  height: 3vh;

  background-color: rgb(152, 211, 198);
  margin: 3px 5vw;
}

.container__buttons button:active {
  background-color: rgb(158, 182, 177);
}

.container__cards {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
}

.container__cart {
  display: flex;
  flex-direction: column;
  position: fixed;
  text-align: center;
  width: 32vw;
  height: 90%;

  top: 5%;
  bottom: 5%;
  left: 66vw;

  align-items: center;

  border: 1px black solid;
}
.container__prices {
  height: 75%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  flex-wrap: wrap;
  align-content: center;
}
.container__total {
  font-size: 20px;
}
</style>
