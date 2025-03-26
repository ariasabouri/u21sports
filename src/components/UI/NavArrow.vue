<template>
    <button class="nav-arrow" :class="{ 'left': direction === 'left', 'right': direction === 'right' }"
        aria-label="Navigation arrow" @click="$emit('click')">
        <img v-if="direction === 'left'" src="@/assets/icons/ph-arrow-circle-left.svg" alt="Previous"
            class="arrow-icon" />
        <img v-else src="@/assets/icons/ph-arrow-circle-right.svg" alt="Next" class="arrow-icon" />
    </button>
</template>

<script setup lang="ts">
defineProps<{
    direction: 'left' | 'right';
}>();

defineEmits<{
    (e: 'click'): void;
}>();
</script>

<style scoped>
.nav-arrow {
    display: flex;
    align-items: center;
    justify-content: center;
    cursor: pointer;
    background: none;
    border: none;
    border-style: none !important;
    box-shadow: none !important;
    outline: none;
    transition: transform 0.3s ease, opacity 0.3s ease;
    opacity: 0.7;
    padding: 10px;
}

.nav-arrow:hover {
    opacity: 1;
    transform: scale(1.1);
}

.arrow-icon {
    width: 32px;
    height: 32px;
}

@media (max-width: 768px) {
    .arrow-icon {
        width: 28px;
        height: 28px;
    }
}

@media (max-width: 480px) {
    .arrow-icon {
        width: 24px;
        height: 24px;
    }
}
</style>