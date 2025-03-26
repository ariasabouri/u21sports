<template>
    <button class="membership-button" :style="{ '--bg-color': backgroundColor }" @click="$emit('click')">
        <div class="button-text">
            <slot>{{ text }}</slot>
        </div>
    </button>
</template>

<script setup lang="ts">
defineProps<{
    text?: string;
    backgroundColor?: string; // Pass hex or "transparent"
}>();

defineEmits<{
    (e: 'click'): void;
}>();
</script>

<style scoped>
.membership-button {
    all: unset;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 10px 30px;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.2s ease;
    background-color: var(--bg-color, #000000);
    color: #ffffff;
    border: 2px solid #ffffff;
    position: relative;
    z-index: 2;
}

.membership-button:hover {
    background-color: #ffffff;
    color: #000000;
    opacity: 1;
}

.button-text {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 600;
    line-height: normal;
    white-space: nowrap;
}
</style>