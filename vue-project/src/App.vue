<template>
  <main>
    <div class="container">
      <div class="texts">
        <div>
          <h1>buy yo groceries here</h1>
          <h1 v-if="number">{{ text }}</h1>

          <ul>
            <li v-for="item in items" :key="item">{{ item }}</li>
          </ul>
        </div>
      </div>

      <div class="cards">
        <Card v-for="products in products" :key="products.title" :title="products.title"
          :description="products.description" :image="products.image" />
      </div>
    </div>
  </main>
</template>

<script>
import Button from "./components/Button.vue";
import Card from "./components/Card.vue";
import {products} from '../src/products';

export default {
  data() {
    return {
   
loggedIn: false,
products,

message: "",
poop: "poop",
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
  justify-content: space-around;
  margin: auto;
}

.cards {
  display: flex;
  flex-direction: column;
}

.texts {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 40vw;
}

.texts input,
button {
  width: 30vw;
}
</style>