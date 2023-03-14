<template>
  <button @click="$emit('button-click')"><slot></slot></button>
</template>

<script>
export default {
  name: "Button",
};
</script>

<style scoped>
button {
  background-color: green;
  width: 450px;
  height: 300px;
}
</style>
