<template>
    <div class="u21-card" :class="{ 'featured': featured }" :style="cardStyle">
        <div v-if="featured && badgeText" class="featured-badge">{{ badgeText }}</div>

        <div class="card-header" v-if="$slots.header || title">
            <slot name="header">
                <h3 v-if="title" class="card-title">{{ title }}</h3>
            </slot>
        </div>

        <div class="card-body">
            <slot></slot>
        </div>

        <div class="card-footer" v-if="$slots.footer">
            <slot name="footer"></slot>
        </div>
    </div>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = withDefaults(defineProps<{
    title?: string;
    featured?: boolean;
    badgeText?: string;
    backgroundColor?: string;
    borderColor?: string;
}>(), {
    backgroundColor: 'var(--color-background-soft)',
    borderColor: 'rgba(255, 255, 255, 0.1)'
});

// Computed style for the card
const cardStyle = computed(() => ({
    backgroundColor: props.backgroundColor,
    borderColor: props.featured ? 'var(--color-primary)' : props.borderColor
}));
</script>

<style scoped>
.u21-card {
    padding: 30px;
    border-radius: 10px;
    background-color: var(--color-background-soft);
    position: relative;
    display: flex;
    flex-direction: column;
    gap: 20px;
    border: 1px solid var(--color-border);
    transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.u21-card:hover {
    box-shadow: 0 8px 30px rgba(0, 0, 0, 0.2);
}

.featured {
    border: 2px solid var(--color-primary);
    transform: scale(1.05);
    z-index: 1;
}

.featured-badge {
    position: absolute;
    top: -12px;
    right: 20px;
    background-color: var(--color-primary);
    color: var(--color-text-secondary);
    padding: 4px 12px;
    border-radius: 20px;
    font-size: 14px;
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
}

.card-title {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 20px;
    margin-bottom: 10px;
    color: var(--color-text);
}

.card-header {
    margin-bottom: 10px;
}

.card-body {
    flex: 1;
}

.card-footer {
    margin-top: auto;
}

@media (max-width: 768px) {
    .u21-card {
        padding: 20px;
    }

    .featured {
        transform: none;
    }
}

@media (max-width: 480px) {
    .u21-card {
        padding: 15px;
    }
}
</style>