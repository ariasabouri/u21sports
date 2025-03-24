<template>
  <footer class="site-footer">
    <!--<div class="nav-section">
      <FooterNav :categories="categories" :backgroundColor="navBackgroundColor" @link-click="handleNavLinkClick" />
    </div>-->
    <div class="info-section">
      <FooterInfo :backgroundColor="infoBackgroundColor" @link-click="handleInfoLinkClick"
        @social-click="handleSocialClick" />
    </div>
  </footer>
</template>

<script setup lang="ts">
import FooterNav from './FooterNav.vue'
import FooterInfo from './FooterInfo.vue'
import { ref } from 'vue'

// Updated categories for football training
const categories = ref([
  {
    title: 'Training',
    links: ['Fußballtraining', 'Athletiktraining', 'Kombi-Training', 'Probetraining']
  },
  {
    title: 'Altersgruppen',
    links: ['U10-U11', 'U12-U13', 'U14-U15']
  },
  {
    title: 'Standorte',
    links: ['Hauptstandort', 'Trainingszeiten', 'Anfahrt', 'Partner']
  },
  {
    title: 'Info & Kontakt',
    links: ['Über Uns', 'Preise', 'Newsletter', 'FAQ']
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