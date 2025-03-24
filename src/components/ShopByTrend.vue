<template>
  <div>
    <!-- Use our new reusable GridSection component -->
    <GridSection
      title="Shop by Trend"
      :gridItems="trendItems"
      ctaText="Shop"
      :columns="2"
      :gap="40"
      :backgroundColor="backgroundColor"
      :textColor="textColor"
      :accentColor="accentColor"
      :prevArrowIcon="prevArrowIcon"
      :nextArrowIcon="nextArrowIcon"
      @prev="handlePrev"
      @next="handleNext"
      @item-click="handleItemClick"
    />
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import GridSection from './GridSection.vue'

// Define arrow icons
const prevArrowIcon = '/src/assets/icons/ph-arrow-circle-left.svg'
const nextArrowIcon = '/src/assets/icons/ph-arrow-circle-right.svg'

// Define styling props that can be customized
const backgroundColor = ref('#0a2025')
const textColor = ref('#ffffff')
const accentColor = ref('#3e9d26')

// Sample data - this could be fetched from an API in a real app
const trendItems = ref([
  {
    title: 'Keni Grace',
    description: 'Explore our futuristic outfit.',
    image: 'https://images.unsplash.com/photo-1539185441755-769473a23570?q=80&w=2971&auto=format&fit=crop'
  },
  {
    title: 'Keni in Paris',
    description: 'Our Paris fashion week trends.',
    image: 'https://images.unsplash.com/photo-1483985988355-763728e1935b?q=80&w=2970&auto=format&fit=crop'
  }
])

// Event handlers
const handlePrev = () => {
  console.log('Previous clicked')
  // Add logic for navigation
}

const handleNext = () => {
  console.log('Next clicked')
  // Add logic for navigation
}

const handleItemClick = (index: number) => {
  console.log(`Item ${index} clicked`)
  // Add logic for item click
}
</script>

<style scoped>
/* No local styles needed as they're defined in the GridSection component */
</style>