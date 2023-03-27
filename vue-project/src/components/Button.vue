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
  color:unset
}
</style>
