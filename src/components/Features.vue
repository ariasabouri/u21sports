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
      <div class="category altersgruppen">
        <h3 class="category-title">Altersgruppen</h3>
        <div class="category-items">
          <div v-for="(item, index) in menItems" :key="index" class="category-item">
            <img class="item-image" :alt="item.title" :src="item.image" />
            <div class="item-content">
              <div class="item-title">{{ item.title }}</div>
              <p class="item-description">{{ item.description }}</p>
              <div class="item-cta" :style="{ color: accentColor }"
                @click="$emit('item-click', { category: 'altersgruppen', index })">
                {{ itemCtaText }}
              </div>
            </div>
          </div>
        </div>
      </div>

      <div class="category trainingsarten">
        <h3 class="category-title">Trainingsarten</h3>
        <div class="category-items">
          <div v-for="(item, index) in womenItems" :key="index" class="category-item">
            <img class="item-image" :alt="item.title" :src="item.image" />
            <div class="item-content">
              <div class="item-title">{{ item.title }}</div>
              <p class="item-description">{{ item.description }}</p>
              <div class="item-cta" :style="{ color: accentColor }"
                @click="$emit('item-click', { category: 'trainingsarten', index })">
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
import kaganImg1 from '@/assets/images/img_kagan_1.jpeg'
import kaganImg2 from '@/assets/images/img_kagan_2.jpeg'
import athletesImg from '@/assets/images/stock/anthomkii_imagine_a_studio_photoshoot_of_professional_athletes__23f93872-3b1c-4f23-845c-ea25f1e1fb63 1.png'

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
  heading: 'Unser Trainingsangebot',
  features: () => [
    {
      title: 'Strukturiertes Training',
      description: ' - Professionell gestaltete Trainingseinheiten für verschiedene Altersgruppen und Leistungsniveaus.'
    },
    {
      title: 'Athletiktraining',
      description: ' - Ganzheitliche Förderung durch spezifisches Athletiktraining für bessere Leistung auf dem Platz.'
    },
    {
      title: 'Individuelle Betreuung',
      description: ' - Persönliche Betreuung durch erfahrene Trainer für optimale Entwicklung.'
    }
  ],
  ctaText: 'Mehr erfahren',
  mainImage: kaganImg1,
  imageAlt: 'Fußballtraining Feature',
  itemCtaText: 'Details',
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26',
  columnGap: 30
})

// Men's items data
const menItems = ref([
  {
    title: 'U10-U11',
    description: 'Grundlegendes Techniktraining und Spielverständnis',
    image: kaganImg1
  },
  {
    title: 'U12-U13',
    description: 'Aufbauendes Training mit taktischen Elementen',
    image: kaganImg2
  },
  {
    title: 'U14-U15',
    description: 'Fortgeschrittenes Training für ambitionierte Spieler',
    image: kaganImg1
  }
])

// Women's items data
const womenItems = ref([
  {
    title: 'Fußballtraining',
    description: 'Technik, Taktik und Spielpraxis',
    image: kaganImg2
  },
  {
    title: 'Athletiktraining',
    description: 'Kraft, Ausdauer und Koordination',
    image: kaganImg1
  },
  {
    title: 'Kombi-Training',
    description: 'Ganzheitliches Training für maximalen Fortschritt',
    image: athletesImg
  }
])

// Define emits
defineEmits<{
  (e: 'cta-click'): void
  (e: 'item-click', payload: { category: 'altersgruppen' | 'trainingsarten', index: number }): void
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
  align-items: flex-start;
  min-height: 90px;
}

.item-image {
  width: 69px;
  height: 69px;
  border-radius: 50%;
  object-fit: cover;
  background-color: #ffffff;
  flex-shrink: 0;
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
    flex-direction: row;
    align-items: center;
    gap: 15px;
    padding: 10px 0;
  }

  .item-image {
    width: 60px;
    height: 60px;
  }

  .item-content {
    gap: 8px;
  }

  .item-description {
    font-size: 13px;
  }
}
</style>