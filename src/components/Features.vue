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
        <img v-if="mainImage" class="feature-image" :alt="imageAlt" :src="mainImage" />
      </slot>
    </div>

    <div class="categories-wrapper">
      <div class="category men">
        <h3 class="category-title">Men</h3>
        <div class="category-items">
          <div v-for="(item, index) in menItems" :key="index" class="category-item">
            <img class="item-image" :alt="item.title" :src="item.image" />
            <div class="item-content">
              <p class="item-description">{{ item.description }}</p>
              <div class="item-cta" :style="{ color: accentColor }"
                @click="$emit('item-click', { category: 'men', index })">
                {{ itemCtaText }}
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="category women">
        <h3 class="category-title">Women</h3>
        <div class="category-items">
          <div v-for="(item, index) in womenItems" :key="index" class="category-item">
            <img class="item-image" :alt="item.title" :src="item.image" />
            <div class="item-content">
              <p class="item-description">{{ item.description }}</p>
              <div class="item-cta" :style="{ color: accentColor }"
                @click="$emit('item-click', { category: 'women', index })">
                {{ itemCtaText }}
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

// Import images
import mainFeatureImage from '@/assets/images/stock/anthomkii_imagine_a_studio_photoshoot_of_professional_athletes__23f93872-3b1c-4f23-845c-ea25f1e1fb63 1.png'
import ellipse1_1 from '@/assets/images/stock/Ellipse 1_1.png'
import ellipse1 from '@/assets/images/stock/Ellipse 1.png'
import ellipse2_1 from '@/assets/images/stock/Ellipse 2_1.png'
import ellipse2_2 from '@/assets/images/stock/Ellipse 2_2.png'
import ellipse2_3 from '@/assets/images/stock/Ellipse 2_3.png'
import ellipse2 from '@/assets/images/stock/Ellipse 2.png'

// Define interfaces for feature and item objects
interface Feature {
  title: string
  description: string
}

interface Item {
  image: string
  title: string
  description: string
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  heading?: string
  features?: Feature[]
  ctaText?: string
  mainImage?: string
  imageAlt?: string
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
      description: ' - Experience the perfect blend of comfort and flexibility with our innovative cushioning technology.'
    },
    {
      title: 'Superior Design',
      description: ' - Stand out with our sleek, modern, and futuristic shoe designs that turn heads wherever you go.'
    },
    {
      title: 'Durability and Quality',
      description: ' - Crafted from high-quality materials, our shoes are designed to last, supporting your athletic pursuits over the long haul.'
    }
  ],
  ctaText: 'Learn more',
  mainImage: mainFeatureImage,
  imageAlt: 'Athletic Performance Feature',
  itemCtaText: 'See product',
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26',
  columnGap: 30
})

// Men's items data
const menItems = ref([
  {
    title: 'Velocity',
    description: 'Exhibit your speed and agility with our \'Velocity\' sports shoes.',
    image: ellipse1_1
  },
  {
    title: 'Unbound',
    description: 'Unleash your potential with the groundbreaking \'Unbound\' running shoes.',
    image: ellipse2_1
  },
  {
    title: 'Futurist',
    description: 'Step into the future with our most advanced model, the \'Futurist\'.',
    image: ellipse2_2
  }
])

// Women's items data
const womenItems = ref([
  {
    title: 'Grace',
    description: 'Embrace comfort and style with our \'Grace\' sports shoes.',
    image: ellipse1
  },
  {
    title: 'Liberate',
    description: 'Break free from the limits with our innovative \'Liberate\' running shoes.',
    image: ellipse2
  },
  {
    title: 'Futurist',
    description: 'Experience the future of sports footwear with our \'Futurist\' model.',
    image: ellipse2_3
  }
])

// Define emits
defineEmits<{
  (e: 'cta-click'): void
  (e: 'item-click', payload: { category: 'men' | 'women', index: number }): void
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
  gap: 30px;
  align-items: flex-start;
}

.feature-text-column {
  flex: 0 1 25%;
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
  flex: 0 1 25%;
  min-width: 280px;
  display: flex;
  align-items: center;
  /* Changed from flex-start to center */
  justify-content: center;
  padding: 20px;
  align-self: stretch;
  /* Added to make it full height */
}

.feature-image {
  width: 100%;
  height: auto;
  object-fit: cover;
  border-radius: 12px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.15);
  transition: transform 0.3s ease;
}

.feature-image:hover {
  transform: scale(1.02);
}

.categories-wrapper {
  flex: 0 1 50%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 30px;
  align-items: start;
}

.category {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.category-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  margin: 0;
}

.category-items {
  display: grid;
  gap: 30px;
}

.category-item {
  display: flex;
  gap: 20px;
  align-items: center;
  min-height: 90px;
}

.item-image {
  width: 69px;
  height: 69px;
  border-radius: 50%;
  object-fit: cover;
  background-color: #ffffff;
}

.item-content {
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.item-description {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  margin: 0;
  line-height: 1.4;
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
@media (max-width: 1400px) {
  .feature-section {
    flex-wrap: wrap;
  }

  .feature-text-column,
  .feature-image-column {
    flex: 1 1 40%;
  }

  .categories-wrapper {
    flex: 1 1 100%;
  }
}

@media (max-width: 1200px) {
  .feature-section {
    flex-direction: column;
    gap: 40px;
    padding: 40px 5%;
  }

  .feature-text-column,
  .feature-image-column,
  .categories-wrapper {
    width: 100%;
  }

  .categories-wrapper {
    flex-direction: column;
  }
}

@media (max-width: 768px) {
  .feature-section {
    flex-direction: column;
    padding: 30px 5%;
  }

  .categories-wrapper {
    grid-template-columns: 1fr;
  }

  .heading-text,
  .category-title {
    font-size: 22px;
  }
}

@media (max-width: 480px) {
  .feature-section {
    padding: 20px 4%;
  }

  .heading-text,
  .category-title {
    font-size: 20px;
  }

  .category-item {
    flex-direction: column;
    align-items: flex-start;
  }

  .item-content {
    width: 100%;
  }
}
</style>