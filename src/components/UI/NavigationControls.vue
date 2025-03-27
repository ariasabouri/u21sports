<template>
    <div class="navigation-controls">
        <img class="nav-arrow" alt="Previous" :src="prevArrowIcon" @click="$emit('prev')" />
        <img class="nav-arrow" alt="Next" :src="nextArrowIcon" @click="$emit('next')" />
    </div>
</template>

<script setup lang="ts">
import arrowLeftIcon from '@/assets/icons/ph-arrow-circle-left.svg'
import arrowRightIcon from '@/assets/icons/ph-arrow-circle-right.svg'

// Define props with defaults
const props = withDefaults(defineProps<{
    prevArrowIcon?: string
    nextArrowIcon?: string
}>(), {
    prevArrowIcon: arrowLeftIcon,
    nextArrowIcon: arrowRightIcon
})

// Define emits
defineEmits<{
    (e: 'prev'): void
    (e: 'next'): void
}>()
</script>

<style scoped>
.navigation-controls {
    display: flex;
    gap: 10px;
    min-width: 106px;
    justify-content: flex-end;
    margin-bottom: 1em;
}

.nav-arrow {
    height: 48px;
    width: 48px;
    cursor: pointer;
    transition: opacity 0.2s ease;
    border-style: none !important;
}

.nav-arrow:hover {
    opacity: 0.8;
}

@media (max-width: 768px) {
    .nav-arrow {
        height: 36px;
        width: 36px;
    }
}

@media (max-width: 480px) {
    .nav-arrow {
        height: 32px;
        width: 32px;
    }
}
</style>