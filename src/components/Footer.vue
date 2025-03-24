<template>
  <footer class="site-footer" :style="{ backgroundColor }">
    <FooterNav 
      :categories="categories"
      :backgroundColor="backgroundColor"
      @link-click="handleLinkClick"
    />
  </footer>
</template>

<script setup lang="ts">
import FooterNav from './FooterNav.vue'
import { ref } from 'vue'

// Define component props with defaults
const props = withDefaults(defineProps<{
  backgroundColor?: string;
}>(), {
  backgroundColor: '#0a2025'
})

// Default categories - could be provided from parent if needed
const categories = ref([
  {
    title: 'Featured',
    links: ['Velocity', 'Unbound', 'Futurist', 'Grace']
  },
  {
    title: 'Shoes',
    links: ['All shoes', 'Velocity Shoes', 'Running Shoes', 'Basketball Shoes']
  },
  {
    title: 'Clothing',
    links: ['All Clothing', 'Tops & T-Shirts', 'Shorts', 'Hoodies & Pullovers']
  },
  {
    title: 'Kids\'',
    links: ['Infant & Toddler Shoes', 'Kids\' Shoes', 'Kids\' Basketball Shoes', 'Kids\' Running Shoes']
  }
])

// Handle link clicks
function handleLinkClick(payload: { category: string, link: string }) {
  console.log(`Clicked ${payload.link} in ${payload.category} category`)
  // Add routing or other actions here
}
</script>

<style scoped>
.site-footer {
  width: 100%;
}
</style>