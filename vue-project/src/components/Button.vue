<template>
  <button @click="$emit('button-click')">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "Button",
};
</script>

<style scoped>
button {
  background-color: rgb(86, 110, 101);
  width: 450px;
  height: 300px;
}
</style>
