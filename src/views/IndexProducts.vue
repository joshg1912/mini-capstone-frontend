<template>
  <div class="index-products">
    <div v-for="product in products" :key="product.id">
      <h1>Name: {{ product.name }}</h1>
      <p>Price: {{ product.price }}</p>
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      products: [],
    };
  },
  created: function () {
    this.indexProducts();
  },
  methods: {
    indexProducts: function () {
      axios.get("http://localhost:3000/products").then((response) => {
        this.products = response.data;
        console.log("All Products:", this.products);
      });
    },
  },
};
</script>
