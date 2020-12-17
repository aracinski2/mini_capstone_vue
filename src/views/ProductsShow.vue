

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <h3>{{ product.name }}</h3>
    <h5>${{ product.price }}</h5>
    <h5>{{ product.description }}</h5>
    <h5>Supplier: {{ product.supplier }}</h5>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Look at this super specific product!",
      product: {},
    };
  },
  created: function () {
    this.productsShow();
  },
  methods: {
    productsShow: function () {
      console.log("products showwww");
      console.log(this.$route.params.id);
      axios.get("/api/products/" + this.$route.params.id).then((response) => {
        console.log(response.data);
        this.product = response.data;
      });
    },
  },
};
</script>
