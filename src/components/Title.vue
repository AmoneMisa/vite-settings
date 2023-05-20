<template>
  <div class="header">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script setup>
defineProps({
  msg: String,
});
</script>

<script>
export default {
  name: "Title"
}
</script>

<style scoped lang="scss">
  .header {
    h1 {
      color: #7a9fc0;
    }
  }
</style>