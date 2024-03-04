<template>
  <div class="home">
    <router-link
      v-for="(product, index) in data"
      :key="index"
      :to="{ name: 'ProductDetail', params: { id: product.id } }"
    >
      <div>
        <img :src="`../assets/kopi.webp`" width="250" alt="" />
        <h3>{{ product.name }}</h3>
        <p>{{ product.price }}</p>
      </div>
    </router-link>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HomeView",
  data() {
    return {
      data: null,
    };
  },
  mounted() {
    axios
      .get("http://localhost:5500/product")
      .then((response) => {
        this.data = response.data.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
