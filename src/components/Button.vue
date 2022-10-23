<template>
  <button class="btn" v-bind:style="{ background: color }">
    {{ text }}
  </button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: {
      type: String,
      default: "Click me",
    },
    color: String,
  }
};
</script>

<style scoped>

</style>
