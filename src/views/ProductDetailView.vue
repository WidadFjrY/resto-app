<template>
  <div>
    <h1>Product Detail</h1>
    <p>Product ID: {{ productId }}</p>
    <p>{{ data }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      productId: null,
      data: null,
    };
  },
  mounted() {
    // Mengambil ID produk dari objek route
    this.productId = this.$route.params.id;
    axios
      .get(`http://localhost:5500/product/${this.productId}`)
      .then((response) => {
        this.data = response.data.data;
      })
      .catch((err) => {
        console.log(err);
      });
  },
};
</script>
