<template>
  <header class="header" :style="headerStyle">
    <div class="header-left">
      <div class="header-logo" @click="$emit('logo-click')">
        <slot name="logo">
          <img
            v-if="logoImage"
            class="logo-image"
            :alt="logoAlt"
            :src="logoImage"
          />
        </slot>
        <div v-if="showBrandName" class="brand-text">
          <div class="brand-name">{{ brandName }}</div>
          <div v-if="brandTagline" class="brand-tagline">{{ brandTagline }}</div>
        </div>
      </div>
      
      <nav class="navigation">
        <slot name="nav-items">
          <div 
            v-for="(item, index) in navItems" 
            :key="index" 
            class="nav-item"
            @click="$emit('nav-click', index)"
          >
            {{ item.label }}
          </div>
        </slot>
      </nav>
    </div>
    
    <div class="header-right">
      <slot name="right-icons">
        <div v-if="rightIcons.length > 0" class="icon-container">
          <img 
            v-for="(icon, index) in rightIcons" 
            :key="index"
            class="header-icon"
            :alt="icon.alt || 'Icon'"
            :src="icon.src"
            @click="$emit('icon-click', index)"
          />
        </div>
      </slot>
    </div>
  </header>
</template>

<script setup lang="ts">
import { computed } from 'vue'

// Define interface for nav item
interface NavItem {
  label: string
  link?: string
  [key: string]: any
}

// Define interface for icon
interface Icon {
  src: string
  alt?: string
  [key: string]: any
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  // Content
  logoImage?: string
  logoAlt?: string
  showBrandName?: boolean
  brandName?: string
  brandTagline?: string
  navItems?: NavItem[]
  rightIcons?: Icon[]
  
  // Styling
  backgroundColor?: string
  textColor?: string
  gradientStart?: string
  gradientEnd?: string
  useGradient?: boolean
}>(), {
  logoImage: '',
  logoAlt: 'Brand Logo',
  showBrandName: true,
  brandName: 'KENI',
  brandTagline: 'SPORTSWEAR',
  navItems: () => [
    { label: 'NEWS & FEATURES' },
    { label: 'MEN' },
    { label: 'WOMEN' },
    { label: 'KIDS' },
    { label: 'ACCESSORIES' },
    { label: 'SALE' }
  ],
  rightIcons: () => [
    { src: '/src/assets/icons/ph-heart.svg', alt: 'Favorites' },
    { src: '/src/assets/icons/ph-shopping-cart.svg', alt: 'Cart' }
  ],
  backgroundColor: '#0a2025',
  textColor: '#ffffff',
  gradientStart: 'rgba(10, 34, 39, 1)',
  gradientEnd: 'rgba(9, 15, 15, 1)',
  useGradient: true
})

// Define emits
defineEmits<{
  (e: 'logo-click'): void
  (e: 'nav-click', index: number): void
  (e: 'icon-click', index: number): void
}>()

// Computed background style
const headerStyle = computed(() => {
  if (props.useGradient) {
    return {
      background: `linear-gradient(90deg, ${props.gradientStart} 0%, ${props.gradientEnd} 100%)`,
      color: props.textColor
    }
  } else {
    return {
      backgroundColor: props.backgroundColor,
      color: props.textColor
    }
  }
})
</script>

<style scoped>
.header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 8%;
  width: 100%;
}

.header-left {
  display: flex;
  align-items: center;
  gap: 60px;
}

.header-logo {
  display: flex;
  align-items: center;
  gap: 11px;
  cursor: pointer;
}

.logo-image {
  height: 38px;
  object-fit: cover;
  max-width: 53px;
}

.brand-text {
  display: flex;
  flex-direction: column;
}

.brand-name {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 20px;
  font-weight: 700;
  line-height: 1.2;
}

.brand-tagline {
  font-family: "Roboto-Black", Helvetica, sans-serif;
  font-size: 13px;
  font-weight: 900;
}

.navigation {
  display: flex;
  align-items: center;
  gap: 40px;
}

.nav-item {
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  white-space: nowrap;
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.nav-item:hover {
  opacity: 0.8;
}

.header-right {
  display: flex;
  align-items: center;
  justify-content: center;
}

.icon-container {
  display: flex;
  align-items: center;
  gap: 20px;
}

.header-icon {
  height: 24px;
  width: 24px;
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.header-icon:hover {
  opacity: 0.8;
}

/* Mobile menu button for responsive design */
.menu-button {
  display: none;
  cursor: pointer;
}

/* Responsive styles */
@media (max-width: 1024px) {
  .header {
    padding: 16px 5%;
  }
  
  .header-left {
    gap: 30px;
  }
  
  .navigation {
    gap: 25px;
  }
}

@media (max-width: 768px) {
  .navigation {
    display: none; /* Hide navigation on mobile - would require mobile menu implementation */
  }
  
  .menu-button {
    display: block;
  }
}

@media (max-width: 480px) {
  .header {
    padding: 12px 4%;
  }
  
  .brand-name {
    font-size: 18px;
  }
  
  .brand-tagline {
    font-size: 11px;
  }
}
</style>