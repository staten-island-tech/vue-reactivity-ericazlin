<template>
  <button @click="$emit('button-click')">
  Add
  </button>
</template>

<script>
export default {
  name: "addButton",
};
</script>

<style scoped>
button {
  width: 10vw;
  padding: 1rem 0;
  background-color: rgb(66, 83, 90);
  margin: 0 0 3vh 0;
}
</style>
