<template>
  <div class="home">
      <!-- <div v-for="product in products" :key="product.id">
      <h4>{{product.name}}</h4> -->
      <div v-for="flow in flowers" :key="flow.id">
      <h4>{{ flow.volumeInfo.title }}</h4>
     <img
       :src="flow.volumeInfo.imageLinks.thumbnail"
       :alt="flow.volumeInfo.title" />
   </div>
  </div>
</template>

<style>
h1 {
  color: brown;
  size: 20px;
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
}
</style>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";
import axios from "axios";

export default {
  name: "home",
   data() {
    return {
      // products: null
      flowers: null
    }
  },
  async mounted() {
    // await axios
      // .get('http//localhost:12345/products')
      // .then(response => this.products = response.data)
       await axios.get('https://www.googleapis.com/books/v1/volumes?q=flowers')
     .then(response => (this.flowers = response.data.items ))
  }
 
};
</script>
