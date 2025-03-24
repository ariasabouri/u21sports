<template>
  <div class="feature-section" :style="sectionStyle">
    <div class="feature-text-column">
      <div class="feature-heading">
        <slot name="heading">
          <h2 class="heading-text">{{ heading }}</h2>
        </slot>
      </div>

      <div class="feature-list">
        <slot name="features">
          <div v-for="(feature, index) in features" :key="index" class="feature-item">
            <span class="feature-highlight" :style="{ color: accentColor }">{{ feature.title }}</span>
            <span class="feature-description">{{ feature.description }}</span>
          </div>
        </slot>
      </div>

      <div v-if="ctaText" class="feature-cta" :style="{ color: accentColor }" @click="$emit('cta-click')">
        {{ ctaText }}
      </div>
    </div>

    <div class="feature-image-column">
      <slot name="image">
        <img
          v-if="mainImage"
          class="feature-image"
          :alt="imageAlt"
          :src="mainImage"
        />
      </slot>
    </div>

    <div class="feature-items-column">
      <slot name="heading-secondary">
        <h3 v-if="secondaryHeading" class="secondary-heading">{{ secondaryHeading }}</h3>
      </slot>

      <slot name="items">
        <div v-for="(item, index) in items" :key="index" class="item-row">
          <img class="item-image" :alt="item.title" :src="item.image" />
          <div class="item-content">
            <p class="item-description">{{ item.description }}</p>
            <div class="item-cta" :style="{ color: accentColor }" @click="$emit('item-click', index)">
              {{ itemCtaText }}
            </div>
          </div>
        </div>
      </slot>
    </div>
  </div>
</template>

<script setup lang="ts">
// Define interfaces for feature and item objects
interface Feature {
  title: string
  description: string
}

interface Item {
  image: string
  title: string
  description: string
  [key: string]: any
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  heading?: string
  features?: Feature[]
  ctaText?: string
  mainImage?: string
  imageAlt?: string
  secondaryHeading?: string
  items?: Item[]
  itemCtaText?: string
  
  // Styling
  backgroundColor?: string
  textColor?: string
  accentColor?: string
  columnGap?: number
}>(), {
  heading: 'Redefining Athletic Performance',
  features: () => [
    {
      title: 'Unmatched Comfort',
      description: '- Experience the perfect blend of comfort and flexibility with our innovative technology.'
    },
    {
      title: 'Superior Design',
      description: '- Stand out with our sleek, modern, and futuristic designs that turn heads wherever you go.'
    },
    {
      title: 'Durability and Quality',
      description: '- Crafted from high-quality materials, our products are designed to last.'
    }
  ],
  ctaText: 'Learn more',
  secondaryHeading: 'Featured Products',
  items: () => [],
  itemCtaText: 'See product',
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26',
  columnGap: 30
})

// Define emits
defineEmits<{
  (e: 'cta-click'): void
  (e: 'item-click', index: number): void
}>()

// Computed styles
const sectionStyle = {
  backgroundColor: props.backgroundColor,
  color: props.textColor,
  gap: `${props.columnGap}px`
}
</script>

<style scoped>
.feature-section {
  display: flex;
  padding: 60px 8%;
  width: 100%;
  flex-wrap: wrap;
}

.feature-text-column {
  flex: 1;
  min-width: 280px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.feature-heading {
  margin-bottom: 20px;
}

.heading-text {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  margin: 0;
}

.feature-list {
  display: flex;
  flex-direction: column;
  gap: 20px;
  margin-bottom: 30px;
}

.feature-item {
  font-size: 14px;
  line-height: 1.5;
}

.feature-highlight {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-weight: 700;
}

.feature-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-weight: 400;
}

.feature-cta {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  width: fit-content;
  transition: opacity 0.2s ease;
}

.feature-cta:hover {
  opacity: 0.8;
}

.feature-image-column {
  flex: 1;
  min-width: 280px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.feature-image {
  width: 100%;
  height: auto;
  object-fit: cover;
}

.feature-items-column {
  flex: 1;
  min-width: 280px;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.secondary-heading {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  margin: 0;
}

.item-row {
  display: flex;
  gap: 20px;
  align-items: center;
}

.item-image {
  width: 69px;
  height: 69px;
  border-radius: 50%;
  object-fit: cover;
}

.item-content {
  display: flex;
  flex-direction: column;
  gap: 10px;
  flex: 1;
}

.item-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  margin: 0;
}

.item-cta {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  cursor: pointer;
  width: fit-content;
  transition: opacity 0.2s ease;
}

.item-cta:hover {
  opacity: 0.8;
}

/* Responsive styles */
@media (max-width: 1200px) {
  .feature-section {
    flex-direction: column;
    gap: 40px;
    padding: 40px 5%;
  }
  
  .feature-text-column,
  .feature-image-column,
  .feature-items-column {
    width: 100%;
  }
}

@media (max-width: 768px) {
  .feature-section {
    padding: 30px 5%;
  }
  
  .heading-text,
  .secondary-heading {
    font-size: 22px;
  }
}

@media (max-width: 480px) {
  .feature-section {
    padding: 20px 4%;
  }
  
  .heading-text,
  .secondary-heading {
    font-size: 20px;
  }
  
  .item-row {
    flex-direction: column;
    align-items: flex-start;
  }
  
  .item-content {
    width: 100%;
  }
}
</style>