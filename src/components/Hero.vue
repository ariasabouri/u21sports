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

// Import background image
import heroBackground from '@/assets/images/stock/hero_basic.png'

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
  titleStart: 'U21 Sports:',
  titleEnd: 'Dein Weg zum besseren Fußballer',
  subtitle: 'Strukturiertes Fußball- und Athletiktraining für alle Altersgruppen. Profitiere von professionellem Training und werde Teil unserer Community.',
  linkText: 'Mehr erfahren',
  ctaText: 'Jetzt anmelden',
  arrowIcon: '/src/assets/icons/ph-arrow-right.svg',
  accentColor: 'var(--color-primary)',
  textColor: 'var(--color-text)',
  backgroundImage: heroBackground
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
  color: var(--color-text);
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
  color: var(--color-text);
}

.hero-title-accent {
  margin-left: 10px;
  color: var(--color-primary);
}

.hero-subtitle {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 18px;
  font-weight: 400;
  line-height: 1.5;
  color: var(--color-text-muted);
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
  color: var(--color-text);
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
  background-color: var(--color-primary);
}

.hero-cta-button:hover {
  background-color: var(--color-primary-hover);
  opacity: 1;
}

.hero-cta-text {
  color: var(--color-text);
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