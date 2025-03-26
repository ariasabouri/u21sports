<template>
  <div class="grid-section" :style="sectionStyle">
    <div class="grid-section-header">
      <div class="section-title">{{ title }}</div>
      <div v-if="showNavigation" class="navigation-controls">
        <slot name="navigation-start">
          <img class="nav-arrow" alt="Previous" :src="prevArrowIcon" @click="$emit('prev')" />
        </slot>
        <slot name="navigation-end">
          <img class="nav-arrow" alt="Next" :src="nextArrowIcon" @click="$emit('next')" />
        </slot>
      </div>
    </div>

    <div class="grid-container" :style="gridContainerStyle">
      <slot>
        <!-- Default grid items if no slot content -->
        <div v-for="(item, index) in gridItems" :key="index" class="grid-item" :style="getGridItemStyle(item)">
          <img class="grid-image" :alt="item.title" :src="item.image" />
          <div class="grid-content">
            <div class="item-title">{{ item.title }}</div>
            <p class="item-description">{{ item.description }}</p>
          </div>
          <div class="item-cta" :style="{ color: accentColor }" @click="$emit('item-click', index)">
            {{ ctaText }}
          </div>
        </div>
      </slot>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// Import arrow icons
import arrowLeftIcon from '@/assets/icons/ph-arrow-circle-left.svg'
import arrowRightIcon from '@/assets/icons/ph-arrow-circle-right.svg'

// Define interface for grid item data
interface GridItem {
  title: string
  description: string
  image: string
  colSpan?: number
  rowSpan?: number
  [key: string]: any
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  title?: string
  gridItems?: GridItem[]
  ctaText?: string

  // Layout options
  columns?: number
  gap?: number
  minWidth?: string
  aspectRatio?: string

  // Navigation
  showNavigation?: boolean
  prevArrowIcon?: string
  nextArrowIcon?: string

  // Styling
  backgroundColor?: string
  textColor?: string
  accentColor?: string
  imageFit?: 'cover' | 'contain' | 'fill'
}>(), {
  title: 'Grid Section',
  gridItems: () => [],
  ctaText: 'Details',
  columns: 2,
  gap: 40,
  minWidth: '280px',
  aspectRatio: '16/9',
  showNavigation: true,
  prevArrowIcon: arrowLeftIcon,
  nextArrowIcon: arrowRightIcon,
  backgroundColor: 'var(--color-background)',
  textColor: 'var(--color-text)',
  accentColor: 'var(--color-primary)',
  imageFit: 'cover'
})

// Define emits
defineEmits<{
  (e: 'prev'): void
  (e: 'next'): void
  (e: 'item-click', index: number): void
}>()

// Computed styles
const sectionStyle = {
  backgroundColor: props.backgroundColor,
  color: props.textColor
}

const gridContainerStyle = computed(() => ({
  display: 'grid',
  gridTemplateColumns: `repeat(${props.columns}, 1fr)`,
  gap: `${props.gap}px`
}))

// Helper function to handle grid item styling based on span properties
const getGridItemStyle = (item: GridItem) => {
  const style: Record<string, string> = {}

  if (item.colSpan) {
    style.gridColumn = `span ${item.colSpan}`
  }

  if (item.rowSpan) {
    style.gridRow = `span ${item.rowSpan}`
  }

  return style
}
</script>

<style scoped>
.grid-section {
  display: flex;
  flex-direction: column;
  gap: 30px;
  padding: 40px 8%;
  width: 100%;
  background-color: var(--color-background);
  color: var(--color-text);
}

.grid-section-header {
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
  color: var(--color-text);
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
  border-style: none !important;
}

.nav-arrow:hover {
  opacity: 0.8;
}

.grid-container {
  display: grid;
  gap: v-bind('`${props.gap}px`');
  grid-template-columns: repeat(auto-fit, minmax(v-bind('props.minWidth'), 1fr));
  width: 100%;
}

.grid-item {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.grid-image {
  width: 100%;
  aspect-ratio: v-bind('props.aspectRatio');
  object-fit: v-bind('props.imageFit');
  border-radius: 8px;
  transition: transform 0.3s ease;
}

.grid-content {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.item-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  color: var(--color-text);
}

.item-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  color: var(--color-text-muted);
}

.item-cta {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  width: fit-content;
  transition: opacity 0.2s ease;
  color: var(--color-primary);
}

.item-cta:hover {
  color: var(--color-primary-hover);
  opacity: 1;
}

/* Responsive styles */
@media (max-width: 1024px) {
  .grid-section {
    padding: 30px 5%;
  }
}

@media (max-width: 768px) {
  .section-title {
    font-size: 20px;
  }

  .nav-arrow {
    height: 36px;
    width: 36px;
  }

  .grid-image {
    min-height: 250px;
  }

  .item-title {
    font-size: 20px;
  }
}

@media (max-width: 480px) {
  .grid-section {
    padding: 20px 4%;
  }

  /* Force single column on mobile */
  .grid-container {
    display: flex !important;
    flex-direction: column !important;
    gap: 40px !important;
  }

  .grid-item {
    gap: 20px;
  }

  .grid-image {
    min-height: 200px;
  }

  .item-title {
    font-size: 18px;
  }
}
</style>