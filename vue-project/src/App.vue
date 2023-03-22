<template>
  <main>
    <div class="container">
      <div class="texts">
        <div>
          <h1>i love shkola</h1>
          <h1 v-if="number">{{ text }}</h1>

          <ul>
            <li v-for="item in items" :key="item">{{ item }}</li>
          </ul>
        </div>

        <div>
          <button @click="authState" v-if="loggedIn">Log Out yo</button>
          <button @click="authState" v-else>Log In yo</button>
        </div>

        <div>
          <input type="text" placeholder="type smth here omg" v-model="message" />
          <p>{{ message }}</p>
        </div>

        <div>
          <h1>{{ time }}</h1>
        </div>

        <Button @button-click="frigginThing">i am a button</Button>
        <p v-if="loggedIn">{{ poop }}</p>
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
      text: "ochen da",
      number: true,
      items: ["I", "am", "an", "array", "being", "iterated"],
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

  computed: {
    time: function () {
      const time = new Date();
      return `${time.getHours()}:${time.getMinutes()}:${time.getSeconds()}`;
    },
  },
  methods: {
    authState: function () {
      if (this.loggedIn === false) {
        this.loggedIn = true;
      } else {
        this.loggedIn = false;
      }
    },
    frigginThing: function () {
      if (this.poop === "") {
        this.poop = "poop";
      } else {
        this.poop = "";
      }
    },
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