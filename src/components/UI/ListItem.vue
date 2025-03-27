<template>
    <li class="u21-list-item" :class="{ 'with-icon': icon }">
        <div v-if="icon" class="list-item-icon">
            <img v-if="typeof icon === 'string'" :src="icon" :alt="iconAlt || 'List item icon'" />
            <component v-else :is="icon"></component>
        </div>
        <div class="list-item-content">
            <slot>{{ text }}</slot>
        </div>
    </li>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
    text?: string;
    icon?: string | object; // Can be a path to image or a component
    iconAlt?: string;
}>();
</script>

<style scoped>
.u21-list-item {
    font-family: "Roboto-Regular", Helvetica, sans-serif;
    font-size: 16px;
    line-height: 1.6;
    margin-bottom: 10px;
    color: var(--color-text);
    display: flex;
    align-items: flex-start;
}

.with-icon {
    gap: 10px;
}

.list-item-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    flex-shrink: 0;
}

.list-item-icon img {
    width: 18px;
    height: 18px;
}

.list-item-content {
    flex: 1;
}
</style>