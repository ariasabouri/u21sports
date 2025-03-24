<template>
  <div class="frame" :style="sectionStyle">
    <div class="header">
      <div class="title">{{ title }}</div>
      <div v-if="showNavigation" class="navigation">
        <img class="nav-arrow" alt="Previous" :src="prevArrowIcon" @click="$emit('prev')" />
        <img class="nav-arrow" alt="Next" :src="nextArrowIcon" @click="$emit('next')" />
      </div>
    </div>

    <div class="content-container">
      <div v-for="(item, index) in items" :key="index" class="content-card">
        <img class="content-image" :alt="item.title" :src="item.image" />
        <div class="content-text">
          <div class="content-title">{{ item.title }}</div>
          <p class="content-description">{{ item.description }}</p>
        </div>
        <div class="content-cta" :style="{ color: accentColor }" @click="$emit('item-click', index)">
          {{ ctaText }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// Import default images
import productImg1 from '@/assets/images/stock/stock_product_img_1.png'
import productImg2 from '@/assets/images/stock/stock_product_img_2.png'
import productImg3 from '@/assets/images/stock/stock_product_img_3.png'
import arrowLeft from '@/assets/icons/ph-arrow-circle-left.svg'
import arrowRight from '@/assets/icons/ph-arrow-circle-right.svg'

// Define interface for content item data
interface ContentItem {
  title: string
  description: string
  image: string
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  title?: string
  items?: ContentItem[]
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
  title: 'Trainingsarten',
  items: () => [
    {
      title: 'Fußballtraining',
      description: 'Technik, Taktik und Spielpraxis.',
      image: productImg1
    },
    {
      title: 'Athletiktraining',
      description: 'Kraft, Ausdauer und Koordination.',
      image: productImg2
    },
    {
      title: 'Kombi-Training',
      description: 'Das komplette Paket für maximalen Erfolg.',
      image: productImg3
    }
  ],
  ctaText: 'Details',
  showNavigation: true,
  prevArrowIcon: arrowLeft,
  nextArrowIcon: arrowRight,
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26'
})

// Define emits
defineEmits<{
  (e: 'prev'): void
  (e: 'next'): void
  (e: 'item-click', index: number): void
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

.content-container {
  display: flex;
  gap: 40px;
  width: 100%;
}

.content-card {
  display: flex;
  flex-direction: column;
  gap: 30px;
  flex: 1;
}

.content-image {
  width: 100%;
  height: 360px;
  object-fit: cover;
}

.content-text {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.content-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
}

.content-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  margin: 0;
}

.content-cta {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  width: fit-content;
  transition: opacity 0.2s ease;
}

.content-cta:hover {
  opacity: 0.8;
}

/* Responsive styles */
@media (max-width: 1024px) {
  .frame {
    padding: 30px 5%;
  }
}

@media (max-width: 768px) {
  .content-container {
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

  .content-image {
    height: 300px;
  }

  .content-title {
    font-size: 20px;
  }
}

@media (max-width: 480px) {
  .frame {
    padding: 20px 4%;
  }

  .content-image {
    height: 250px;
  }
}
</style>