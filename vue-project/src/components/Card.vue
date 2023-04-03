<template>
  <div class="card">
    <h2>{{ title }}</h2>
    <img :src="getImage" alt="" />
    <p>${{ price }}</p>
    <addButton @button-click="addToCart()"/>
  </div>
</template>

<script>
import addButton from "./addButton.vue";


export default {
  name: "Card",

  methods: {
    addToCart() {
      this.$emit("addToCart", { title: this.title, price: this.price });
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
.card {
  border: 1px black solid;
  display: flex;
  flex-direction: column;
  width: 20vw;
  height: auto;
  align-items: center;
  margin: 1rem;
}

.card img {
  width: 18vw;
  height: 400px;
  object-fit: contain;
}
</style>
