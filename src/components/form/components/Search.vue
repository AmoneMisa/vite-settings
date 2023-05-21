<template>
  <div class="search-holder">
    <div class="search-input">
      <input type="search" class="input input_search" v-model="name" placeholder="T-short Blue...">
    </div>
    <div class="search-numbers">
      <input type="number" min="1" class="input input_number" v-model.number="minPrice" placeholder="Min">
      <input type="number" class="input input_number" v-model.number="maxPrice" placeholder="Max">
    </div>
  </div>
</template>

<script>
export default {
  name: "Search",
  props: {
    filter: Object
  },
  computed: {
    name: {
      get() {
        return this.filter.name;
      },
      set(value) {
        this.$emit("update:filter", {...this.filter, name: value});
      }
    },
    minPrice: {
      get() {
        return this.filter.minPrice;
      },
      set(value) {
        this.$emit("update:filter", {...this.filter, minPrice: value});
      }
    },
    maxPrice: {
      get() {
        return this.filter.maxPrice;
      },
      set(value) {
        this.$emit("update:filter", {...this.filter, maxPrice: value});
      }
    }
  },
  emits: ["update:filter"]
}
</script>

<style scoped lang="scss">
.search-input {
  margin-bottom: 10px;
}

.input_search {
  max-width: 680px;
  width: 100%;
  margin: 0 auto;
}

.input_number {
  max-width: 60px;

  &:not(:last-child) {
    margin-right: 10px;
  }
}
</style>