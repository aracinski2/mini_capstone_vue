

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <div v-for='product in products'>
      <router-link v-bind:to="`/products/${product.id}`">
      <h3>{{ product.name }}</h3>
      </router-link>
      <h5>${{ product.price }}</h5>
      <h5>{{ product.description }}</h5><br>
    </div>
  </div>
</template>

<style>
</style>

<script>
import axios from "axios";

export default {
  data: function () {
    return {
      message: "Welcome to my store!",
      products: [],
    };
  },
  created: function () {
    this.productsIndex();
  },
  methods: {
    productsIndex: function () {
      console.log("ooo shiny products");
      axios.get("/api/products").then((response) => {
        console.log(response.data);
        this.products = response.data;
      });
    },
  },
};
</script>
