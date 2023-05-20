<template>
  <div class="product" :data-id="product.id" :data-category="product.category">
    <div class="product__image-holder" v-if="product.image">
      <custom-image :src="product.image"/>
    </div>
    <div class="product__title">{{ product.title }}</div>
    <div class="product__description">{{ product.description }}</div>
    <div class="product__price">{{ product.price }} $</div>
    <div class="product__rating" v-if="product.rating">
      <div class="product__rating-rate">{{ product.rating.rate }} &#11088</div>
      <div class="product__rating-count">{{ product.rating.count }} - Total votes</div>
    </div>
  </div>
</template>

<script>
import Image from "./common/Image.vue";

export default {
  name: "ProductItem",
  components: {CustomImage: Image},
  props: {
    product: {}
  }
}
</script>

<style scoped>
.product {
  width: 100%;
  background: #fafafa;
  border-radius: 18px;
  box-shadow: #1a1a1a 1px 1px 1px;
  color: #213547;
  padding: 12px;
  height: 300px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.product__image-holder {
  width: 120px;
  height: 120px;
  margin: 0 auto 15px;
}

.product__description {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-size: 12px;
}
</style>