<template>
  <div class="products-list">
    <div class="products-list__item" v-for="product in foundItems">
      <product-item :product="product"/>
    </div>
  </div>
</template>

<script>
import ProductItem from "./ProductItem.vue";

export default {
  name: "ProductsList",
  components: {ProductItem},
  props: {
    products: Array,
    filter: Object
  },
  computed: {
    foundItems() {
      if (!this.filter) {
        return this.products;
      }

      return this.products.filter(product => {
        if (this.filter.name && !product.title.toLowerCase().includes(this.filter.name.toLowerCase())) {
          return false;
        }

        if (this.filter.minPrice && product.price < this.filter.minPrice) {
          return false;
        }

        // noinspection RedundantIfStatementJS
        if (this.filter.maxPrice && product.price > this.filter.maxPrice) {
          return false
        }

        return true;
      });
    }
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
  width: 100%;
}
</style>