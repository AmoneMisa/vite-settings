<template>
  <label>
    <input v-bind="$attrs" class="input" />
    <slot />
  </label>
</template>

<script>
export default {
  name: "Input",
}
</script>

<style lang="scss">
  .input {
    padding: 8px;
    border-radius: 8px;
    border: 1px solid #213547;
    width: 180px;

    &::placeholder {
      color: #f9f9f9;
    }
  }

  input[type="checkbox"] {
    width: 20px;
  }
</style>