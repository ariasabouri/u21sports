<template>
    <button :class="['u21-button', `u21-button--${variant}`, { 'u21-button--exempt': exempt }]"
        :style="{ '--bg-color': backgroundColor }" @click="$emit('click')">
        <div class="u21-button__text">
            <slot>{{ text }}</slot>
        </div>
    </button>
</template>

<script setup lang="ts">
defineProps<{
    text?: string;
    backgroundColor?: string; // Pass hex or "transparent"
    variant?: 'primary' | 'secondary' | 'action' | 'nav'; // Different button styles
    exempt?: boolean; // Whether to exempt from global styles
}>();

defineEmits<{
    (e: 'click'): void;
}>();
</script>

<style scoped>
/* Base button styles with BEM naming convention */
.u21-button {
    all: unset;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: var(--u21-btn-padding, 10px 30px);
    border-radius: var(--u21-btn-border-radius, 10px);
    cursor: pointer;
    transition: var(--u21-btn-transition, all 0.3s ease);
    position: relative;
    z-index: 2;
    font-family: "Roboto", sans-serif;
    font-weight: var(--u21-btn-font-weight, 600);
    font-size: var(--u21-btn-font-size, 14px);
}

/* Primary variant */
.u21-button--primary {
    background-color: var(--bg-color, #000000);
    color: var(--app-text, #ffffff);
    border: 2px solid var(--app-accent, #ffffff);
}

.u21-button--primary:hover {
    background-color: var(--app-accent, #ffffff);
    color: var(--app-background, #000000);
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(255, 255, 255, 0.2);
}

/* Secondary variant */
.u21-button--secondary {
    background-color: transparent;
    color: var(--app-text, #ffffff);
    border: 2px solid var(--app-accent, #ffffff);
}

.u21-button--secondary:hover {
    background-color: rgba(255, 255, 255, 0.1);
    transform: translateY(-2px);
}

/* Action variant (for prominent actions) */
.u21-button--action {
    background-color: var(--bg-color, var(--app-accent, #ffffff));
    color: var(--app-background, #000000);
    border: 2px solid var(--app-accent, #ffffff);
    font-weight: 700;
}

.u21-button--action:hover {
    background-color: var(--app-accent-hover, #f0f0f0);
    transform: translateY(-2px);
    box-shadow: 0 4px 8px rgba(255, 255, 255, 0.4);
}

/* Navigation button variant */
.u21-button--nav {
    background: none;
    border: none;
    box-shadow: none;
    opacity: 0.7;
    padding: 8px 16px;
}

.u21-button--nav:hover {
    opacity: 1;
    transform: none;
}

/* Button text */
.u21-button__text {
    white-space: nowrap;
}

/* Active state for all buttons */
.u21-button:active {
    transform: translateY(0);
}
</style>