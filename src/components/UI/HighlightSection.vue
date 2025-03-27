<template>
  <section class="highlight-section" :style="cssVars">
    <h2 v-if="title">{{ title }}</h2>
    <p v-if="text">{{ text }}</p>
    <div class="buttons" v-if="buttons && buttons.length">
      <button v-for="(button, index) in buttons" :key="index" class="cta-button" @click="button.onClick">
        {{ button.label }}
      </button>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

interface Button {
  label: string;
  onClick?: () => void;
  class?: string;
}

const props = withDefaults(defineProps<{
  title?: string;
  text?: string;
  backgroundColor?: string;
  textColor?: string;
  textAlign?: 'left' | 'center' | 'right';
  buttons?: Button[];
}>(), {
  backgroundColor: 'var(--color-primary)',
  textColor: 'var(--color-text-secondary)',
  textAlign: 'center'
});

// Define CSS variables from props for unified styling.
const cssVars = computed(() => ({
  '--section-background': props.backgroundColor,
  '--section-text-color': props.textColor,
  textAlign: props.textAlign
}));
</script>

<style scoped>
.highlight-section {
  margin-bottom: 30px;
  padding: 25px;
  border-radius: 10px;
  background-color: var(--section-background);
  color: var(--section-text-color);
  border: 1px solid var(--color-border);
}

.highlight-section h2 {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  margin-bottom: 15px;
  color: var(--section-text-color);
}

.highlight-section p {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 20px;
  color: var(--section-text-color);
}

.highlight-section .cta-button {
  all: unset;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 12px 30px;
  border-radius: 10px;
  cursor: pointer;
  transition: opacity 0.2s ease;
  background-color: var(--section-text-color);
  color: var(--color-primary);
  font-family: "Roboto-SemiBold", Helvetica, sans-serif;
  font-size: 14px;
  font-weight: 600;
  margin-top: 20px;
}

.highlight-section .cta-button:hover {
  opacity: 0.9;
}

@media (max-width: 768px) {
  .highlight-section {
    padding: 20px;
  }

  .highlight-section h2 {
    font-size: 20px;
    margin-bottom: 15px;
  }
}

@media (max-width: 480px) {
  .highlight-section {
    padding: 15px;
    margin-bottom: 20px;
  }

  .highlight-section h2 {
    font-size: 18px;
  }

  .highlight-section p,
  .highlight-section li {
    font-size: 14px;
  }
}
</style>