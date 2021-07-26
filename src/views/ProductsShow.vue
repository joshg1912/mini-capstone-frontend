<template>
  <div class="show-product">
    <div>
      <h1>{{ product.name }}</h1>
      <p>{{ product.price }}</p>
      <p>{{ product.description }}</p>
      <img v-bind:src="product.image_url" alt="product.title" />
    </div>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      product: {},
    };
  },
  created: function () {
    axios.get("/products/" + this.$route.params.id).then((response) => {
      this.product = response.data;
      console.log("Product:", response.data);
    });
  },
};
</script>
