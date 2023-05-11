<template>
  <div class="header">
    <h1>{{ msg }}</h1>
    <input v-model="someText">
    <div class="body-text">
      <span>"{{ someText }}" - I was wrote this string!</span>
    </div>
  </div>
</template>

<script setup>
defineProps({
  msg: String,
});
</script>

<script>
export default {
  name: "NewTestComponent",
  data() {
    return {
      someText: "Try to write something!"
    }
  }
}
</script>

<style scoped lang="scss">
  .body-text {
    span {
      color: #646cff;
    }
  }

  input {
    background: aliceblue;
    border: 1px solid #646cff;
    border-radius: 4px;
    color: #1a1a1a;
    padding: 10px;
    margin-bottom: 15px;
  }
</style>