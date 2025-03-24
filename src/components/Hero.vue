<template>
  <div class="hero" :style="bgImageStyle">
    <div class="hero-content">
      <div class="hero-text">
        <!-- Use slot for title with fallback -->
        <slot name="title">
          <h1 class="hero-title">
            <span class="hero-title-primary">{{ titleStart }}</span>
            <span class="hero-title-accent">{{ titleEnd }}</span>
          </h1>
        </slot>

        <!-- Use slot for subtitle with fallback -->
        <slot name="subtitle">
          <p class="hero-subtitle">{{ subtitle }}</p>
        </slot>
      </div>

      <div class="hero-cta-container">
        <!-- Link text with optional icon -->
        <div v-if="linkText" class="hero-link">
          <span class="hero-link-text">{{ linkText }}</span>
          <slot name="linkIcon">
            <img v-if="arrowIcon" class="hero-arrow-icon" alt="Arrow right" src="@/assets/icons/ph-arrow-right.svg" />
          </slot>
        </div>

        <!-- Primary CTA button -->
        <button v-if="ctaText" class="hero-cta-button" :style="{ backgroundColor: accentColor }"
          @click="$emit('cta-click')">
          <span class="hero-cta-text">{{ ctaText }}</span>
        </button>

        <!-- Additional slot for custom CTAs -->
        <slot name="cta"></slot>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// Using script setup for composition API
import { computed } from 'vue'

// Define props with defaults for flexibility
const props = withDefaults(defineProps<{
  // Text content
  titleStart?: string
  titleEnd?: string
  subtitle?: string
  linkText?: string
  ctaText?: string

  // Image/icon paths
  backgroundImage?: string
  arrowIcon?: string

  // Styling
  accentColor?: string
  textColor?: string
}>(), {
  // Default values
  titleStart: 'Redefining Motion:',
  titleEnd: 'The Future of Footwear is Here',
  subtitle: 'Experience unparalleled comfort and innovative design with our state-of-the-art products.',
  linkText: 'Step into the Future',
  ctaText: 'Shop Now',
  arrowIcon: '/src/assets/icons/ph-arrow-right.svg',
  accentColor: '#3e9d26',
  textColor: '#ffffff',
  backgroundImage: '/src/assets/images/stock/hero_basic.png'
})

// Define emits
defineEmits<{
  (e: 'cta-click'): void
}>()

// Computed background style
const bgImageStyle = computed(() => ({
  backgroundImage: `url(${props.backgroundImage})`,
  color: props.textColor
}))
</script>

<style scoped>
.hero {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  background-position: center;
  background-size: cover;
  min-height: 600px;
  width: 100%;
  padding: 40px 8%;
  position: relative;
  background-image: url('@/assets/images/stock/hero_basic.png');
  /* Fallback image */
}

.hero-content {
  display: flex;
  flex-direction: column;
  gap: 60px;
  justify-content: center;
  max-width: 650px;
}

.hero-text {
  display: flex;
  flex-direction: column;
  gap: 20px;
  width: 100%;
}

.hero-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 42px;
  font-weight: 700;
  line-height: 1.2;
  margin: 0;
}

.hero-title-primary {
  color: var(--hero-text-color, #ffffff);
}

.hero-title-accent {
  color: var(--hero-accent-color, #3e9d26);
}

.hero-subtitle {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 18px;
  font-weight: 400;
  line-height: 1.5;
  color: var(--hero-text-color, #ffffff);
}

.hero-cta-container {
  display: flex;
  align-items: center;
  gap: 20px;
  flex-wrap: wrap;
}

.hero-link {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
}

.hero-link-text {
  color: var(--hero-text-color, #ffffff);
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  white-space: nowrap;
}

.hero-arrow-icon {
  height: 24px;
  width: 24px;
}

.hero-cta-button {
  all: unset;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 12px 30px;
  border-radius: 10px;
  cursor: pointer;
  transition: opacity 0.2s ease;
  background-color: var(--hero-accent-color, #3e9d26);
}

.hero-cta-button:hover {
  opacity: 0.9;
}

.hero-cta-text {
  color: #ffffff;
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  white-space: nowrap;
}

/* Responsive styles */
@media (max-width: 768px) {
  .hero {
    padding: 30px 5%;
  }

  .hero-content {
    gap: 40px;
    max-width: 100%;
  }

  .hero-title {
    font-size: 32px;
  }

  .hero-subtitle {
    font-size: 16px;
  }
}

@media (max-width: 480px) {
  .hero {
    min-height: 500px;
    padding: 20px 5%;
  }

  .hero-content {
    gap: 30px;
  }

  .hero-title {
    font-size: 28px;
  }
}
</style>