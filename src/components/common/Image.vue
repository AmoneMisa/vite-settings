<template>
  <img class="image" :src="src">
</template>

<script>
export default {
  name: "Image",
  props: {
    src: String
  }
}
</script>

<style scoped>
.image {
  max-width: 100%;
  max-height: 100%;
  width: 100%;
  margin: auto;
}
</style>