<template>
  <div class="membership-section" :style="sectionStyle">
    <div class="membership-header">
      <slot name="section-title">
        <div class="section-title">{{ sectionTitle }}</div>
      </slot>
    </div>

    <div class="membership-banner" :style="bannerStyle">
      <div class="banner-content">
        <div class="banner-text">
          <slot name="banner-heading">
            <div class="banner-heading">{{ bannerHeading }}</div>
          </slot>
          <slot name="banner-subheading">
            <p class="banner-subheading">{{ bannerSubheading }}</p>
          </slot>
        </div>

        <div class="banner-actions">
          <slot name="banner-actions">
            <button class="membership-button" :style="buttonStyle" @click="$emit('join-click')">
              <div class="button-text">{{ joinButtonText }}</div>
            </button>

            <button class="membership-button" :style="buttonStyle" @click="$emit('signin-click')">
              <div class="button-text">{{ signinButtonText }}</div>
            </button>
          </slot>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  sectionTitle?: string
  bannerHeading?: string
  bannerSubheading?: string
  joinButtonText?: string
  signinButtonText?: string

  // Styling
  backgroundColor?: string
  textColor?: string
  accentColor?: string
  bannerBackgroundImage?: string
  buttonBackgroundColor?: string
  paddingX?: string
  paddingY?: string
}>(), {
  sectionTitle: 'Keni Membership',
  bannerHeading: 'BECOME A MEMBER',
  bannerSubheading: 'Sign up for free. Join the community.',
  joinButtonText: 'Join Us',
  signinButtonText: 'Sign In',
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  accentColor: '#3e9d26',
  bannerBackgroundImage: '/src/assets/images/membership-banner.png',
  buttonBackgroundColor: '#ffffff',
  paddingX: '8%',
  paddingY: '40px'
})

// Define emits
defineEmits<{
  (e: 'join-click'): void
  (e: 'signin-click'): void
}>()

// Computed styles
const sectionStyle = computed(() => ({
  backgroundColor: props.backgroundColor,
  color: props.textColor,
  padding: `0 ${props.paddingX} ${props.paddingY}`
}))

const bannerStyle = computed(() => ({}))

const buttonStyle = computed(() => ({
  backgroundColor: props.buttonBackgroundColor,
  color: props.accentColor
}))
</script>

<style scoped>
.membership-section {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 30px;
  width: 100%;
}

.membership-header {
  display: flex;
  align-items: center;
  width: 100%;
  padding: 10px 0;
}

.section-title {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  font-weight: 700;
  line-height: normal;
}

.membership-banner {
  display: flex;
  align-items: center;
  width: 100%;
  padding: 40px;
  border-radius: 10px;
  background-color: rgba(62, 157, 38, 0.85);
  min-height: 300px;
  position: relative;
}

.membership-banner::after {
  content: '';
  position: absolute;
  top: 0;
  right: 0;
  width: 40%;
  height: 100%;
  background-image: url('@/assets/images/shoe.png');
  background-position: center;
  background-repeat: no-repeat;
  background-size: auto;
  z-index: 1;
}

.banner-content {
  display: flex;
  flex-direction: column;
  gap: 40px;
  max-width: 50%;
  align-items: flex-start;
}

.banner-text {
  display: flex;
  flex-direction: column;
  gap: 10px;
  align-items: flex-start;
  text-align: left;
}

.banner-heading {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 48px;
  font-weight: 700;
  line-height: normal;
}

.banner-subheading {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 20px;
  font-weight: 400;
  line-height: normal;
  margin: 0;
}

.banner-actions {
  display: flex;
  align-items: center;
  gap: 20px;
}

.membership-button {
  all: unset;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
  padding: 10px 30px;
  border-radius: 10px;
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.membership-button:hover {
  opacity: 0.9;
}

.button-text {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  line-height: normal;
  white-space: nowrap;
}

/* Responsive styles */
@media (max-width: 1024px) {
  .membership-section {
    padding: 0 5% 30px;
  }

  .membership-banner {
    padding: 30px;
  }
}

@media (max-width: 768px) {
  .banner-heading {
    font-size: 36px;
  }

  .banner-subheading {
    font-size: 18px;
  }
}

@media (max-width: 480px) {
  .membership-section {
    padding: 0 4% 20px;
  }

  .membership-banner {
    padding: 20px;
  }

  .banner-heading {
    font-size: 28px;
  }

  .banner-subheading {
    font-size: 16px;
  }

  .banner-actions {
    flex-direction: column;
    width: 100%;
  }

  .membership-button {
    width: 100%;
  }
}
</style>