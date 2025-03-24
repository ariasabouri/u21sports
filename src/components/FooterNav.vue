<template>
  <div class="footer-nav" :style="{ backgroundColor }">
    <div v-for="(category, index) in categories" :key="index" class="footer-category">
      <div class="category-title">{{ category.title }}</div>
      <div class="category-links">
        <div v-for="(link, linkIndex) in category.links" :key="linkIndex"
          :class="['category-link', linkIndex === 0 ? 'category-link-first' : '']"
          @click="$emit('link-click', { category: category.title, link })">
          {{ link }}
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
interface Category {
  title: string;
  links: string[];
}

// Define component props with defaults
const props = withDefaults(defineProps<{
  categories?: Category[];
  backgroundColor?: string;
}>(), {
  categories: () => [
    {
      title: 'Training',
      links: ['Fußballtraining', 'Athletiktraining', 'Kombi-Training', 'Probetraining']
    },
    {
      title: 'Altersgruppen',
      links: ['U10-U11', 'U12-U13', 'U14-U15']
    },
    {
      title: 'Informationen',
      links: ['Über Uns', 'Standorte', 'Preise', 'Urban Sports Club']
    },
    {
      title: 'Kontakt',
      links: ['Anmeldung', 'Newsletter', 'FAQ', 'Kontaktformular']
    }
  ],
  backgroundColor: '#0a2025'
})

// Define emits for link clicks
defineEmits<{
  (e: 'link-click', payload: { category: string, link: string }): void
}>()
</script>

<style scoped>
.footer-nav {
  display: flex;
  align-items: flex-start;
  gap: 80px;
  justify-content: center;
  padding: 0px 140px 80px;
  width: 100%;
  box-sizing: border-box;
}

.footer-category {
  display: inline-flex;
  flex-direction: column;
  gap: 20px;
  position: relative;
}

.category-title {
  color: #ffffff;
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 700;
  line-height: normal;
  position: relative;
}

.category-links {
  display: inline-flex;
  flex-direction: column;
  gap: 10px;
  position: relative;
}

.category-link {
  color: #ffffff;
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 400;
  line-height: normal;
  position: relative;
  cursor: pointer;
  transition: opacity 0.2s;
}

.category-link:hover {
  opacity: 0.8;
}

.category-link-first {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  margin-top: -1px;
}

/* Responsive styles */
@media (max-width: 1024px) {
  .footer-nav {
    padding: 0px 80px 60px;
    gap: 60px;
  }
}

@media (max-width: 768px) {
  .footer-nav {
    padding: 0px 40px 40px;
    gap: 40px;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .footer-category {
    width: calc(50% - 20px);
    margin-bottom: 20px;
  }
}

@media (max-width: 480px) {
  .footer-nav {
    padding: 0px 20px 30px;
    flex-direction: column;
    gap: 30px;
  }

  .footer-category {
    width: 100%;
    margin-bottom: 0;
  }
}
</style>