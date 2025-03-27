<template>
    <router-link :to="to" class="u21-nav-link" :class="{ 'u21-nav-link--active': isActive, 'u21-button--exempt': true }"
        @click="$emit('click')">
        <slot>{{ text }}</slot>
    </router-link>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { useRoute } from 'vue-router';

const props = defineProps<{
    to: string;
    text?: string;
    exact?: boolean;
}>();

const route = useRoute();
const isActive = computed(() => {
    // Special handling for home route
    if (props.to === '/') {
        return route.path === '/';
    }
    // For other routes, check if the current path starts with this route
    return route.path.startsWith(props.to);
});

defineEmits<{
    (e: 'click'): void;
}>();
</script>

<style scoped>
.u21-nav-link {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 600;
    white-space: nowrap;
    cursor: pointer;
    transition: opacity 0.2s ease;
    text-decoration: none !important;
    color: inherit;
    position: relative;
    padding-bottom: 2px;
    /* Add exemption to prevent global styles from affecting links */
    text-decoration: none !important;
}

.u21-nav-link:hover {
    opacity: 0.8;
}

.u21-nav-link--active {
    font-weight: 700;
    opacity: 1;
}

.u21-nav-link--active::after {
    content: '';
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 100%;
    height: 2px;
    background-color: #ffffff;
}

.u21-nav-link:not(.u21-nav-link--active):hover::after {
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

@media (max-width: 768px) {
    .u21-nav-link {
        font-size: 18px;
    }
}

@media (max-width: 480px) {
    .u21-nav-link {
        font-size: 16px;
    }
}
</style>