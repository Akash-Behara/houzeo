<script setup>
import NavBar from './components/NavBar.vue'
import HouseDetailBanner from './components/HouseDetailBanner.vue';

import  HouseDetails from './pages/houseDetails/housedetails.vue'
</script>

<template>
  <header class="nav">
    <NavBar />
    <HouseDetailBanner />
  </header>
  <main class="main">
    <HouseDetails />
  </main>
</template>

<style scoped>
.nav{
  position: sticky;
  top: 0;
  width: 100%;
  z-index: 999;
}
.main{
  margin-top: 20px;
}

</style>
