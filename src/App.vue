<script setup>
import ProductsList from "./components/ProductsList.vue";
</script>

<template>
  <div class="page">
    <custom-title msg="Just take a look at this items!"/>
    <div class="page__products-list">
      <products-list :products="products"/>
    </div>
  </div>
</template>

<script>
import Title from "./components/Title.vue";

export default {
  async created() {
    this.products = await fetch("https://fakestoreapi.com/products").then(res => res.json());
  },
  components: {
    customTitle: Title
  },
  data() {
    return {
      products: []
    }
  }
}
</script>

<style scoped>

</style>
