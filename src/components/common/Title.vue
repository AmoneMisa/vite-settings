<template>
  <div class="header-title">
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
  .header-title {
      color: #7a9fc0;
  }
</style>