<template>
<select class="select" v-bind="$attrs">
  <option :name="option.name" :id="option.id" v-for="option in options">{{ option.value }}</option>
</select>
</template>

<script>
export default {
  name: "Select",
  props: {
    options: Array,
    value: String
  }
}
</script>

<style scoped>
  .select {
    padding: 8px;
    border-radius: 8px;
    border: 1px solid #213547;
    width: 200px;
  }
</style>