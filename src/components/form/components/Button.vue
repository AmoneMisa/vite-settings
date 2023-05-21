<template>
  <button class="button" v-bind="$attrs">
    <slot />
  </button>
</template>

<script>
export default {
  name: "Button"
}
</script>

<style lang="scss">
  .button {
    background: #7a9fc0;

    &:not(.close) {
      max-width: 240px;
      min-width: 200px;
      margin: 0 auto;
    }
  }
</style>