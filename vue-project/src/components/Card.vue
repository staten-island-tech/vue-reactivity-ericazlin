<template>
  <div class="card">
    <h2>{{ title }}</h2>
    <img :src="getImage" alt="" />
    <p>{{ description }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    title: String,
    description: String,
    image: String,
  },
  computed: {
    getImage: function () {
      return this.image;
    }
  }
};
</script>

<style>
.card {
  border: 1px black solid;
  display: flex;
  flex-direction: column;
  width: fit-content;
  align-items: center;
  margin: 1rem;
}

.card img {
  width: 600px;
}
</style>
