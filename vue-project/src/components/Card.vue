<template>
  <div class="card">
    <h2>{{ title }}</h2>
    <img :src="getImage" alt="" />
    <p>PRICE: ${{ price }}</p>
    <input type="number" v-model="message" placeholder="type your quantity" />
    <addButton @button-click="addToCart()" />
  </div>
</template>

<script>
import addButton from "./addButton.vue";

export default {
  name: "Card",

  data() {
    return {
      message: "",
    };
  },

  methods: {
    addToCart() {
      console.log(this.message);
      if (this.message <= 0) {
        this.message = "";
      } else if (this.message == "") {
        this.$emit("addToCart", {
          title: this.title,
          price: this.price,
          quantity: 1,
        });
        this.message = "";
      } else {
        this.$emit("addToCart", {
          title: this.title,
          price: this.price,
          quantity: this.message,
        });
        this.message = "";
      }
    },
  },

  props: {
    title: String,
    price: Number,
    image: String,
  },
  computed: {
    getImage: function () {
      return this.image;
    },
  },
  components: {
    addButton,
  },
};
</script>

<style>
input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  display: none;
}
.card {
  border: 1px black solid;

  display: flex;
  flex-direction: column;
  align-items: center;

  width: 18vw;
  height: auto;

  padding: 1rem;
  margin: 0.5rem;
}

.card img {
  width: 18vw;
  height: 300px;
  object-fit: contain;
}

.card h2 {
  font-size: 35px;
}

.card p {
  font-size: 20px;
  margin-bottom: 1rem;
}

.card input {
  margin-bottom: 1rem;
}
</style>
