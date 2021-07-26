<template>
  <div class="create-product">
    <form v-on:submit.prevent="createProduct()">
      <h1>Create A Product</h1>
      <ul>
        <li v-for="error in errors" v-bind:key="error">{{ error }}</li>
      </ul>
      <div>
        <label>Name:</label>
        <input type="text" v-model="newProductParams.name" />
      </div>
      <div>
        <label>Price:</label>
        <input type="text" v-model="newProductParams.price" />
      </div>
      <div>
        <label>Image_url:</label>
        <input type="text" v-model="newProductParams.image_url" />
      </div>
      <div>
        <label>Description</label>
        <input type="text" v-model="newProductParams.description" />
      </div>
      <div>
        <label>Supplier ID</label>
        <input type="text" v-model="newProductParams.supplier_id" />
      </div>
      <input type="submit" value="Submit" />
    </form>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data: function () {
    return {
      errors: [],
      newProductParams: {},
    };
  },
  methods: {
    createProduct: function () {
      axios.post("http://localhost:3000/products", this.newProductParams).then((response) => {
        console.log("Success!", response.data);
        this.products.push(response.data);
      });
    },
  },
};
</script>
