<template>
  <div class="vld-parent">
    <loading 
        :active.sync="isLoading" 
        :can-cancel="true" 
        :on-cancel="onCancel"
        :is-full-page="fullPage"></loading>
    <h1>Магазин</h1>
    <button @click="getProductData()">{{ buttonName }}</button>
    <ul class="product-list">
      <product-item 
        v-for="productData in productDataList" 
        :key="productData.id" 
        :productData="productData"
      ></product-item>
    </ul> 
  </div>
</template>

<script setup>
  import ProductItem from "./components/ProductItem.vue";
  import axios from "axios";
  import Loading from 'vue-loading-overlay';
  import 'vue-loading-overlay/dist/css/index.css';
  import { ref } from "vue";

  const isLoading = ref(false)
  const fullPage = ref(true)
  const doAjax = () => {
        isLoading.value = true;
        setTimeout(() => {
          isLoading.value = false
        },5000)
    }
  const onCancel = () => {
      isLoading.value = false;
  }

  const productDataList = ref ([])
  const buttonName = ref ('Загрузить данные')

  function getProductData() {
    doAjax()
    axios
      .get("https://fakestoreapi.com/products")
      .then(response => (this.productDataList = response.data));
    buttonName.value = 'Обновить данные'
    onCancel()
  }
</script>

<style>
  body {
    padding: 2rem;
    font-family: 'Just Another Hand', cursive;
    background: #f3f3f3;
  }
</style>