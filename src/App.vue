<script setup lang="ts">
import { RouterView } from 'vue-router'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Promo from './components/Promo.vue'
</script>

<template>
  <Promo />
  <Header />
  <RouterView />
  <Footer />
</template>

<style>
/* Add any global styles here */
</style>
