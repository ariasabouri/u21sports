<template>
  <section class="highlight-section">
    <slot name="icon"></slot>
    <h2 v-if="title">{{ title }}</h2>
    <slot name="content">
      <p v-if="text">{{ text }}</p>
    </slot>
    <slot name="footer"></slot>
  </section>
</template>

<script setup lang="ts">
defineProps<{
  title?: string;
  text?: string;
}>();
</script>

<style scoped>
.highlight-section {
  margin-bottom: 30px;
  padding: 25px;
  border-radius: 10px;
  background-color: #FFFFFF;
  color: var(--color-text-secondary);
  border: 1px solid var(--color-border);
}

.highlight-section h2 {
  font-family: "Roboto-Bold", Helvetica, sans-serif;
  font-size: 24px;
  margin-bottom: 15px;
  color: var(--color-text-secondary);
}

.highlight-section p {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 20px;
  color: var(--color-text-secondary);
}

.highlight-section ul {
  list-style-type: disc;
  padding-left: 20px;
  margin-bottom: 20px;
}

.highlight-section li {
  font-family: "Roboto-Regular", Helvetica, sans-serif;
  font-size: 16px;
  line-height: 1.6;
  margin-bottom: 10px;
  color: var(--color-text-secondary);
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