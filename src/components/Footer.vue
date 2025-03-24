<template>
  <footer class="site-footer">
    <div class="nav-section">
      <FooterNav 
        :categories="categories"
        :backgroundColor="navBackgroundColor"
        @link-click="handleNavLinkClick"
      />
    </div>
    <div class="info-section">
      <FooterInfo
        :backgroundColor="infoBackgroundColor"
        @link-click="handleInfoLinkClick"
        @social-click="handleSocialClick"
      />
    </div>
  </footer>
</template>

<script setup lang="ts">
import FooterNav from './FooterNav.vue'
import FooterInfo from './FooterInfo.vue'
import { ref } from 'vue'

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

const navBackgroundColor = '#0a2025'
const infoBackgroundColor = '#449596'

// Handle navigation link clicks
function handleNavLinkClick(payload: { category: string, link: string }) {
  console.log(`Clicked ${payload.link} in ${payload.category} category`)
  // Add routing or other actions here
}

// Handle info link clicks
function handleInfoLinkClick(payload: { section: string, link: string }) {
  console.log(`Clicked ${payload.link} in ${payload.section} section`)
  // Add routing or other actions here
}

// Handle social media clicks
function handleSocialClick(socialNetwork: string) {
  console.log(`Clicked ${socialNetwork} social icon`)
  // Add social media redirect logic here
}
</script>

<style scoped>
.site-footer {
  width: 100%;
}

.nav-section {
  background-color: #0a2025;
  width: 100%;
}

.info-section {
  background-color: #449596;
  width: 100%;
}
</style>