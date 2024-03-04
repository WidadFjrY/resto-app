<template>
  <div class="home">
    <div class="landing">
      <div class="content">
        <h1>Ngineep Company Profile Website</h1>
        <p>Hospitality Template - One page simple minimalist</p>
        <button>Learn More</button>
      </div>
      <img src="@/assets/image.png" alt="" />
    </div>

    <div class="product">
      <div class="filter">
        <p>Product Type</p>
        <div class="checkbox">
          <input type="checkbox" name="type" id="type" />
          <h5>Compeny Profile Website</h5>
        </div>
      </div>
      <div class="menu">
        <router-link
          class="card"
          v-for="(product, index) in data"
          :key="index"
          :to="{ name: 'ProductDetail', params: { id: product.id } }"
          exact
        >
          <div>
            <img src="@/assets/kopi.webp" alt="" />
            <h3>{{ product.name }}</h3>
            <p>{{ product.price }}</p>
          </div>
        </router-link>
      </div>
    </div>
  </div>
</template>

<style scoped>
.landing {
  background-color: #f1f1f1;
  height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 288px;
}

.landing .content {
  width: 774px;
  height: 243px;
}

.landing .content h1 {
  font-size: 42px;
  font-weight: 700;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.landing .content p {
  font-size: 24px;
  font-weight: 700;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.landing .content button {
  padding: 12px 48px;
  background-color: #ed3237;
  border-radius: 6px;
  border: none;
  color: white;
  font-size: 16px;
  font-weight: 600;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
.landing img {
  width: 400px;
  border-radius: 16px;
}

.product {
  margin-top: 100px;
  display: flex;
  padding: 0 48px;
}

.product .filter p {
  font-weight: 600;
  font-size: 18px;
  color: #00000080;
}

.product .filter h5 {
  font-weight: 600;
  font-size: 18px;
  margin-right: 222px;
  margin-bottom: 0;
}

.menu {
  width: 1, 356px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.checkbox {
  display: flex;
  align-items: center;
  gap: 8px;
}

.menu .card {
  width: 370.56px;
  overflow: hidden;
  height: 460.71px;
  border: none;
}

.menu .card h3 {
  margin-top: 19px;
  font-size: 25.35px;
  font-weight: 400;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  text-decoration: none;
}

.menu .card p {
  margin-top: 13px;
  color: #00000099;
  font-weight: 400;
  font-size: 18px;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.menu img {
  width: 432.56;
  height: 324.02px;
  object-fit: cover;
  text-decoration: none;
}
</style>

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
