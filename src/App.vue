<template>
  <div id="app">
    <navbar></navbar>
    <router-view />
    <footer-view></footer-view>
  </div>
</template>

<script>
import Navbar from "./components/NavBar.vue";
import FooterView from "./components/Footer.vue";
export default {
  components: { Navbar, FooterView },
};
</script>
