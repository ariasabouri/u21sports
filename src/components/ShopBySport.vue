<template>
  <div class="frame" :style="sectionStyle">
    <div class="header">
      <div class="title">{{ title }}</div>
      <div v-if="showNavigation" class="navigation">
        <img class="nav-arrow" alt="Previous" :src="prevArrowIcon" @click="$emit('prev')" />
        <img class="nav-arrow" alt="Next" :src="nextArrowIcon" @click="$emit('next')" />
      </div>
    </div>

    <div class="sports-container">
      <div v-for="(sport, index) in sportsItems" :key="index" class="sport-card">
        <img class="sport-image" :alt="sport.title" :src="sport.image" />
        <div class="sport-content">
          <div class="sport-title">{{ sport.title }}</div>
          <p class="sport-description">{{ sport.description }}</p>
        </div>
        <div class="sport-cta" :style="{ color: accentColor }" @click="$emit('sport-click', index)">
          {{ ctaText }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// Define interface for sport item data
interface SportItem {
  title: string
  description: string
  image: string
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  title?: string
  sportsItems?: SportItem[]
  ctaText?: string

  // Navigation
  showNavigation?: boolean
  prevArrowIcon?: string
  nextArrowIcon?: string

  // Styling
  backgroundColor?: string
  textColor?: string
  accentColor?: string
}>(), {
  title: 'Shop by Sport',
  sportsItems: () => [
    {
      title: 'Keni Golf',
      description: 'Everything you need for any course.',
      image: '/src/assets/images/stock/stock_product_img_1.png'
    },
    {
      title: 'Keni Basketball',
      description: 'Styles made for your games.',
      image: '/src/assets/images/stock/stock_product_img_2.png'
    },
    {
      title: 'Keni Trail Running',
      description: 'Everything you need for adventure.',
      image: '/src/assets/images/stock/stock_product_img_3.png'
    }
  ],
  ctaText: 'Shop',
  showNavigation: true,
  prevArrowIcon: '/src/assets/icons/ph-arrow-circle-left.svg',
  nextArrowIcon: '/src/assets/icons/ph-arrow-circle-right.svg',
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26'
})

// Define emits
defineEmits<{
  (e: 'prev'): void
  (e: 'next'): void
  (e: 'sport-click', index: number): void
}>()

// Computed styles
const sectionStyle = computed(() => ({
  backgroundColor: props.backgroundColor,
  color: props.textColor
}))
</script>

<style scoped>
.frame {
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 40px 8%;
  width: 100%;
}

.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  white-space: nowrap;
}

.navigation {
  display: flex;
  gap: 10px;
}

.nav-arrow {
  height: 48px;
  width: 48px;
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.nav-arrow:hover {
  opacity: 0.8;
}

.sports-container {
  display: flex;
  gap: 40px;
  width: 100%;
}

.sport-card {
  display: flex;
  flex-direction: column;
  gap: 30px;
  flex: 1;
}

.sport-image {
  width: 100%;
  height: 360px;
  object-fit: cover;
}

.sport-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.sport-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
}

.sport-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  margin: 0;
}

.sport-cta {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  width: fit-content;
  transition: opacity 0.2s ease;
}

.sport-cta:hover {
  opacity: 0.8;
}

/* Responsive styles */
@media (max-width: 1024px) {
  .frame {
    padding: 30px 5%;
  }
}

@media (max-width: 768px) {
  .sports-container {
    flex-direction: column;
    gap: 40px;
  }

  .title {
    font-size: 20px;
  }

  .nav-arrow {
    height: 36px;
    width: 36px;
  }

  .sport-image {
    height: 300px;
  }

  .sport-title {
    font-size: 20px;
  }
}

@media (max-width: 480px) {
  .frame {
    padding: 20px 4%;
  }

  .sport-image {
    height: 250px;
  }
}
</style>