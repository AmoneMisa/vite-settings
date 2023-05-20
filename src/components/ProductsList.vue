<template>
  <div class="products-list">
    <div class="products-list__item" v-for="product in products">
      <product-item :product="product" />
    </div>
  </div>
</template>

<script>
import ProductItem from "./ProductItem.vue";

export default {
  name: "ProductsList",
  components: {ProductItem},
  props: {
    products: []
  }
}
</script>

<style scoped>
  .products-list {
    display: flex;
    flex-wrap: wrap;
    margin-left: -15px;
  }

  .products-list__item {
    margin-left: 15px;
    max-width: 340px;
    padding: 12px;
  }
</style>