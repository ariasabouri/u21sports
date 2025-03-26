<template>
  <header class="header" :style="headerStyle">
    <!-- Logo section -->
    <router-link to="/" class="header-logo" @click="closeMobileMenu">
      <slot name="logo">
        <img v-if="logoImage" class="logo-image" :alt="logoAlt" :src="logoImage" />
      </slot>
      <div v-if="showBrandName" class="brand-text">
        <div class="brand-name">{{ brandName }}</div>
        <div v-if="brandTagline" class="brand-tagline">{{ brandTagline }}</div>
      </div>
    </router-link>

    <!-- Navigation and right content section -->
    <div class="header-right-content">
      <!-- Hamburger menu button -->
      <button class="menu-button" @click="toggleMobileMenu" :class="{ 'is-active': isMobileMenuOpen }">
        <span class="hamburger-line"></span>
        <span class="hamburger-line"></span>
        <span class="hamburger-line"></span>
      </button>

      <nav class="navigation" :class="{ 'is-open': isMobileMenuOpen }">
        <slot name="nav-items">
          <router-link v-for="(item, index) in navItems" :key="index" :to="item.route" class="nav-item"
            active-class="nav-item-active" @click="closeMobileMenu">
            {{ item.label }}
          </router-link>
        </slot>
      </nav>

      <div class="icons-section">
        <slot name="right-icons">
          <div v-if="rightIcons.length > 0" class="icon-container">
            <img v-for="(icon, index) in rightIcons" :key="index" class="header-icon" :alt="icon.alt || 'Icon'"
              :src="icon.src" @click="$emit('icon-click', index)" />
          </div>
        </slot>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { computed, ref } from 'vue'

// Define interface for nav item
interface NavItem {
  label: string
  route: string
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
  logoAlt: 'U21 Sports Logo',
  showBrandName: true,
  brandName: 'U21',
  brandTagline: 'SPORTS',
  navItems: () => [
    { label: 'HOME', route: '/' },
    // { label: 'TRAININGSARTEN', route: '/training-types' },
    // { label: 'UNSERE TRAINER', route: '/trainers' },
    // { label: 'UNSERE ATHLETEN', route: '/athletes' },
    { label: 'ÜBER UNS', route: '/about' },
    { label: 'TRAINING', route: '/training' },
    { label: 'ALTERSGRUPPEN', route: '/age-groups' },
    { label: 'STANDORTE', route: '/locations' },
    { label: 'PREISE', route: '/pricing' },
    { label: 'KONTAKT', route: '/contact' }
  ],
  rightIcons: () => [],
  backgroundColor: 'var(--color-header)',
  textColor: 'var(--color-text)',
  gradientStart: 'var(--color-header)',
  gradientEnd: 'var(--color-background-soft)',
  useGradient: true
})

// Define emits
defineEmits<{
  (e: 'logo-click'): void
  (e: 'nav-click', index: number): void
  (e: 'icon-click', index: number): void
}>()

// Mobile menu state
const isMobileMenuOpen = ref(false)

// Toggle mobile menu
const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

// Close mobile menu
const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}

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
  position: relative;
}

.header-right-content {
  display: flex;
  align-items: center;
  gap: 40px;
  margin-left: auto;
}

.header-logo {
  display: flex;
  align-items: center;
  gap: 11px;
  cursor: pointer;
  text-decoration: none;
  color: inherit;
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
  text-decoration: none;
  color: inherit;
  position: relative;
  padding-bottom: 2px;
}

.nav-item-active {
  color: var(--color-text);
  font-weight: 700;
}

.nav-item-active::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: #ffffff;
  transform-origin: center;
  transform: scaleX(1);
}

.nav-item:not(.nav-item-active):hover::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 100%;
  height: 2px;
  background-color: rgba(255, 255, 255, 0.5);
  transform-origin: center;
  transform: scaleX(0);
  transition: transform 0.3s ease;
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

/* Mobile menu button */
.menu-button {
  display: none;
  flex-direction: column;
  justify-content: space-between;
  width: 30px;
  height: 20px;
  background: none;
  border: none;
  padding: 0;
  cursor: pointer;
  position: relative;
  z-index: 100;
  margin-right: -2em;
}

.hamburger-line {
  width: 100%;
  height: 2px;
  background-color: var(--color-text);
  transition: all 0.3s ease;
}

.menu-button.is-active .hamburger-line:nth-child(1) {
  transform: translateY(9px) rotate(45deg);
}

.menu-button.is-active .hamburger-line:nth-child(2) {
  opacity: 0;
}

.menu-button.is-active .hamburger-line:nth-child(3) {
  transform: translateY(-9px) rotate(-45deg);
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
  .header-right-content {
    flex: 1;
    justify-content: flex-end;
    margin-right: -5px;
  }

  .menu-button {
    display: flex;
  }

  .navigation {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: rgba(10, 32, 37, 0.98);
    flex-direction: column;
    justify-content: center;
    align-items: center;
    gap: 20px;
    z-index: 90;
    padding: 80px 20px;
    transition: opacity 0.3s ease, visibility 0.3s ease;
  }

  .navigation.is-open {
    display: flex;
    opacity: 1;
    visibility: visible;
  }

  .nav-item {
    font-size: 18px;
  }

  .header-right {
    display: none;
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

  .navigation.is-open {
    padding: 60px 20px;
  }

  .nav-item {
    font-size: 16px;
  }
}
</style>