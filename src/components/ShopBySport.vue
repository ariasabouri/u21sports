<template>
  <div class="card-section" :style="sectionStyle">
    <div class="card-section-header">
      <div class="section-title">{{ title }}</div>
      <div v-if="showNavigation" class="navigation-controls">
        <slot name="navigation-start">
          <img 
            class="nav-arrow" 
            alt="Previous" 
            :src="prevArrowIcon" 
            @click="$emit('prev')" 
          />
        </slot>
        <slot name="navigation-end">
          <img 
            class="nav-arrow" 
            alt="Next" 
            :src="nextArrowIcon" 
            @click="$emit('next')" 
          />
        </slot>
      </div>
    </div>
    
    <div class="card-container" :style="{ gap: `${cardGap}px` }">
      <slot>
        <!-- Default cards as fallback if no slots are provided -->
        <div 
          v-for="(card, index) in cards" 
          :key="index" 
          class="card"
        >
          <img 
            class="card-image" 
            :alt="card.title" 
            :src="card.image" 
            :style="{ height: `${cardImageHeight}px` }"
          />
          <div class="card-content">
            <div class="card-title">{{ card.title }}</div>
            <p class="card-description">{{ card.description }}</p>
          </div>
          <div 
            class="card-cta" 
            :style="{ color: accentColor }"
            @click="$emit('card-click', index)"
          >
            {{ ctaText }}
          </div>
        </div>
      </slot>
    </div>
  </div>
</template>

<script setup lang="ts">
// Define prop types with interface for card data
interface Card {
  title: string
  description: string
  image: string
  [key: string]: any // Allow for additional properties
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  title?: string
  cards?: Card[]
  ctaText?: string
  
  // Navigation
  showNavigation?: boolean
  prevArrowIcon?: string
  nextArrowIcon?: string
  
  // Styling
  backgroundColor?: string
  textColor?: string
  accentColor?: string
  cardGap?: number
  cardImageHeight?: number
}>(), {
  title: 'Featured Items',
  cards: () => [],
  ctaText: 'Shop',
  showNavigation: true,
  prevArrowIcon: '/src/assets/icons/ph-arrow-circle-left.svg',
  nextArrowIcon: '/src/assets/icons/ph-arrow-circle-right.svg',
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26',
  cardGap: 40,
  cardImageHeight: 360
})

// Define emits
defineEmits<{
  (e: 'prev'): void
  (e: 'next'): void
  (e: 'card-click', index: number): void
}>()

// Computed styles
const sectionStyle = {
  backgroundColor: props.backgroundColor,
  color: props.textColor
}
</script>

<style scoped>
.card-section {
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 40px 8%;
  width: 100%;
}

.card-section-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
}

.section-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  white-space: nowrap;
}

.navigation-controls {
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

.card-container {
  display: flex;
  width: 100%;
  overflow-x: auto;
  scroll-behavior: smooth;
  /* Hide scrollbar but keep functionality */
  -ms-overflow-style: none;  /* IE and Edge */
  scrollbar-width: none;  /* Firefox */
}

.card-container::-webkit-scrollbar {
  display: none; /* Chrome, Safari, Opera */
}

.card {
  display: flex;
  flex-direction: column;
  gap: 30px;
  flex: 1;
  min-width: 250px;
}

.card-image {
  width: 100%;
  object-fit: cover;
}

.card-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.card-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
}

.card-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  white-space: normal;
}

.card-cta {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  width: fit-content;
  transition: opacity 0.2s ease;
}

.card-cta:hover {
  opacity: 0.8;
}

/* Responsive styles */
@media (max-width: 768px) {
  .card-section {
    padding: 30px 5%;
  }
  
  .card {
    min-width: 200px;
  }
}

@media (max-width: 480px) {
  .card-section {
    padding: 20px 4%;
  }
  
  .section-title {
    font-size: 20px;
  }
  
  .nav-arrow {
    height: 36px;
    width: 36px;
  }
  
  .card {
    min-width: 180px;
    gap: 20px;
  }
  
  .card-title {
    font-size: 20px;
  }
}
</style>