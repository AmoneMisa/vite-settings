<script setup>
import ProductsList from "./components/ProductsList.vue";
import CreateOrderForm from "./components/form/CreateOrderForm.vue";
</script>

<template>
  <div class="page">
    <div class="page-header">
      <custom-header v-model:filter="filter"/>
    </div>
    <div class="page__products-list">
      <div class="page__add-product">
        <custom-button @click="isShowProductForm = true">Add new product</custom-button>
      </div>
      <div class="page__create-order">
        <custom-button @click="isShowOrderForm = true">Create order</custom-button>
      </div>
      <products-list :products="products" :filter="filter"/>
    </div>

    <div class="form-popup" v-show="isShowProductForm">
      <div class="form-popup__background"></div>
      <div class="form-popup__body">
        <custom-button class="form-popup__close close" @click="isShowProductForm=false">x</custom-button>
        <custom-form :inputs="addProductForm" button-msg="Add new product" @submit:form="e => addProduct(e)"/>
      </div>
    </div>
    <div class="form-popup" v-show="isShowOrderForm">
      <div class="form-popup__background"></div>
      <div class="form-popup__body">
        <custom-button class="form-popup__close close" @click="isShowOrderForm=false">x</custom-button>
        <create-order-form @submit:form="isShowOrderForm=false"/>
      </div>
    </div>
  </div>
</template>

<script>
import Title from "./components/common/Title.vue";
import Header from "./components/layout/Header.vue";
import Form from "./components/form/components/Form.vue";
import Button from "./components/form/components/Button.vue";

export default {
  async created() {
    this.products = await fetch("https://fakestoreapi.com/products").then(res => res.json());
  },
  components: {
    customTitle: Title,
    customHeader: Header,
    CustomForm: Form,
    CustomButton: Button
  },
  data() {
    return {
      products: [],
      filter: {
        name: "",
        minPrice: "",
        maxPrice: ""
      },
      isShowProductForm: false,
      isShowOrderForm: false,
      addProductForm: [
        {type: "number", placeholder: "Id for product", name: "id", required: true},
        {type: "text", placeholder: "Title for product", name: "title"},
        {type: "text", placeholder: "Description for product", name: "description", required: true},
        {
          type: "select", placeholder: "Category for product", name: "category", required: true, options: [{
            id: 1,
            value: "Laptops",
            name: "laptops"
          }, {
            id: 2,
            value: "Clothes",
            name: "clothes"
          }, {
            id: 3,
            value: "Toys",
            name: "toys"
          }, {
            id: 4,
            value: "Windows",
            name: "windows"
          }]
        },
        {type: "number", placeholder: "Price for product", name: "price", required: true},
        {type: "url", placeholder: "Image for product (URL)", name: "image"},
      ]
    }
  },
  methods: {
    addProduct(product) {
      if (!product) {
        return;
      }

      if (this.products.includes(product)) {
        return;
      }

      this.products.push(JSON.parse(product));
    }
  }
}
</script>

<style scoped lang="scss">
.page__add-product,
.page__create-order {
  margin-bottom: 15px;
}

.form-popup {
  position: fixed;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  z-index: 999;
}

.form-popup__background {
  width: 100vw;
  height: 100vh;
  background: #242424;
  opacity: 0.3;
  overflow: hidden;
  position: absolute;
  z-index: -1;
}

.form-popup__body {
  background: #f9f9f9;
  color: #213547;
  border-radius: 18px;
  position: absolute;
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  width: 400px;
  height: 300px;
  margin: auto;
  padding: 15px 40px 15px 15px;
}

.close {
  position: absolute;
  font-size: 14px;
  padding: 4px 8px;
  right: 60px;
  top: 10px;
  background: transparent ;
  color: #7a9fc0;
}
</style>
