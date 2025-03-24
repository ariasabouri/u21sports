<template>
  <div class="footer-info" :style="{ backgroundColor }">
    <div class="info-container">
      <div class="links-section">
        <div class="primary-links">
          <div v-for="(link, index) in primaryLinks" :key="index"
            :class="[index === 0 ? 'primary-link-first' : 'primary-link']"
            @click="$emit('link-click', { section: 'primary', link })">
            {{ link }}
          </div>
        </div>

        <div class="help-section">
          <div class="section-title">{{ helpTitle }}</div>
          <div class="section-links">
            <div v-for="(link, index) in helpLinks" :key="index"
              :class="[index === 0 ? 'section-link-first' : 'section-link']"
              @click="$emit('link-click', { section: 'help', link })">
              {{ link }}
            </div>
          </div>
        </div>

        <div class="about-section">
          <div class="section-title">{{ aboutTitle }}</div>
          <div class="section-links">
            <div v-for="(link, index) in aboutLinks" :key="index"
              :class="[index === 0 ? 'section-link-first' : 'section-link']"
              @click="$emit('link-click', { section: 'about', link })">
              {{ link }}
            </div>
          </div>
        </div>
      </div>

      <div class="social-icons">
        <img v-for="(icon, index) in socialIcons" :key="index" class="social-icon" :src="icon.src" :alt="icon.alt"
          @click="$emit('social-click', icon.name)" />
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
// Import icons as modules
import twitterIcon from '@/assets/icons/ph-twitter-logo.svg'
import facebookIcon from '@/assets/icons/ph-facebook-logo.svg'
import youtubeIcon from '@/assets/icons/ph-youtube-logo.svg'
import instagramIcon from '@/assets/icons/ph-instagram-logo.svg'

interface SocialIcon {
  name: string;
  src: string;
  alt: string;
}

const props = withDefaults(defineProps<{
  backgroundColor?: string;
  primaryLinks?: string[];
  helpTitle?: string;
  helpLinks?: string[];
  aboutTitle?: string;
  aboutLinks?: string[];
  socialIcons?: SocialIcon[];
}>(), {
  backgroundColor: '#449596',
  primaryLinks: () => [
    'Probetraining',
    'Newsletter',
    'Standorte',
    'Anmeldung',
    'Unser Blog',
    'Feedback'
  ],
  helpTitle: 'Hilfe',
  helpLinks: () => [
    'Buchungsstatus',
    'Trainingszeiten',
    'Stornierung',
    'Zahlungsoptionen',
    'Gutscheine',
    'Kontakt'
  ],
  aboutTitle: 'Über U21 Sports',
  aboutLinks: () => [
    'News',
    'Karriere',
    'Partner',
    'Philosophie',
    'Nachhaltigkeit'
  ],
  socialIcons: () => [
    {
      name: 'twitter',
      src: twitterIcon,
      alt: 'Twitter Logo'
    },
    {
      name: 'facebook',
      src: facebookIcon,
      alt: 'Facebook Logo'
    },
    {
      name: 'youtube',
      src: youtubeIcon,
      alt: 'YouTube Logo'
    },
    {
      name: 'instagram',
      src: instagramIcon,
      alt: 'Instagram Logo'
    }
  ]
})

// Define emits
defineEmits<{
  (e: 'link-click', payload: { section: string, link: string }): void
  (e: 'social-click', socialNetwork: string): void
}>()
</script>

<style scoped>
.footer-info {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  padding: 40px 140px 80px;
  width: 100%;
  box-sizing: border-box;
}

.info-container {
  display: flex;
  justify-content: space-between;
  width: 100%;
}

.links-section {
  display: inline-flex;
  gap: 80px;
}

.primary-links {
  display: inline-flex;
  flex-direction: column;
  gap: 10px;
  position: relative;
}

.primary-link-first,
.primary-link {
  color: #ffffff;
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 700;
  line-height: normal;
  white-space: nowrap;
  width: fit-content;
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.primary-link-first {
  margin-top: -1px;
}

.primary-link-first:hover,
.primary-link:hover {
  opacity: 0.8;
}

.help-section,
.about-section {
  display: inline-flex;
  flex-direction: column;
  gap: 20px;
  position: relative;
}

.section-title {
  color: #ffffff;
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 700;
  line-height: normal;
  margin-top: -1px;
}

.section-links {
  display: inline-flex;
  flex-direction: column;
  gap: 10px;
}

.section-link-first,
.section-link {
  color: #ffffff;
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: normal;
  cursor: pointer;
  transition: opacity 0.2s ease;
}

.section-link-first {
  margin-top: -1px;
}

.section-link-first:hover,
.section-link:hover {
  opacity: 0.8;
}

.social-icons {
  display: inline-flex;
  gap: 20px;
  align-items: flex-end;
}

.social-icon {
  height: 24px;
  width: 24px;
  cursor: pointer;
  transition: opacity 0.2s ease, transform 0.2s ease;
}

.social-icon:hover {
  opacity: 0.8;
  transform: scale(1.1);
}

/* Responsive styles */
@media (max-width: 1024px) {
  .footer-info {
    padding: 40px 80px 60px;
  }

  .links-section {
    gap: 60px;
  }
}

@media (max-width: 768px) {
  .footer-info {
    padding: 30px 40px 40px;
  }

  .info-container {
    flex-direction: column;
    gap: 40px;
  }

  .links-section {
    gap: 40px;
    flex-wrap: wrap;
  }

  .social-icons {
    justify-content: center;
  }
}

@media (max-width: 600px) {
  .links-section {
    flex-direction: column;
    gap: 30px;
  }

  .help-section,
  .about-section {
    gap: 15px;
  }
}
</style>