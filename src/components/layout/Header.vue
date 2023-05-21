<template>
  <div class="header">
    <custom-title msg="Just take a look at this items!"/>
    <search :filter="filter" @update:filter="$emit('update:filter', $event)" />
  </div>
</template>

<script>
import Title from "../common/Title.vue";
import Search from "../form/components/Search.vue";

export default {
  name: "Header",
  components: {
    Search,
    customTitle: Title
  },
  props: {
    filter: Object
  },
  emits: ["update:filter"]
}
</script>

<style scoped>
  .header {
    margin-bottom: 20px;
  }
</style>