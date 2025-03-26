<template>
    <router-link :to="to" class="nav-link" :class="{ 'active': isActive }" @click="$emit('click')">
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
.nav-link {
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
}

.nav-link:hover {
    opacity: 0.8;
}

.nav-link.active {
    font-weight: 700;
    opacity: 1;
}

.nav-link.active::after {
    content: '';
    position: absolute;
    bottom: -2px;
    left: 0;
    width: 100%;
    height: 2px;
    background-color: #ffffff;
}

@media (max-width: 768px) {
    .nav-link {
        font-size: 18px;
    }
}

@media (max-width: 480px) {
    .nav-link {
        font-size: 16px;
    }
}
</style>