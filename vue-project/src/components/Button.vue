<template>
  <button @click="$emit('button-click')">
    <slot>Add</slot>
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
  background-color: rgb(145, 87, 116);
  margin: 0 0 3vh 0;
}
</style>
