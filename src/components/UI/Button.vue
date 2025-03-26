<template>
    <button class="u21-button" :class="{
        'primary': type === 'primary',
        'secondary': type === 'secondary',
        'large': size === 'large',
        'small': size === 'small'
    }" @click="$emit('click')">
        <div class="button-text">
            <slot>{{ text }}</slot>
        </div>
    </button>
</template>

<script setup lang="ts">
defineProps<{
    text?: string;
    type?: 'primary' | 'secondary';
    size?: 'small' | 'medium' | 'large';
}>();

defineEmits<{
    (e: 'click'): void;
}>();
</script>

<style scoped>
.u21-button {
    all: unset;
    display: inline-flex;
    align-items: center;
    justify-content: center;
    gap: 10px;
    padding: 10px 30px;
    border-radius: 10px;
    cursor: pointer;
    transition: opacity 0.2s ease;
    background-color: #000000 !important;
    color: #ffffff !important;
    border: 2px solid #ffffff !important;
    position: relative;
    z-index: 2;
}

.u21-button:hover {
    background-color: #ffffff !important;
    color: #000000 !important;
    opacity: 1;
}

.u21-text {
    font-family: "Roboto-SemiBold", Helvetica, sans-serif;
    font-size: 14px;
    font-weight: 600;
    line-height: normal;
    white-space: nowrap;
}

.u21-button.large {
    padding: 12px 40px;
}

.u21-button.large .button-text {
    font-size: 16px;
}

.u21-button.small {
    padding: 8px 20px;
}

.u21-button.small .button-text {
    font-size: 12px;
}

.u21-button.secondary {
    border: 1px solid rgba(255, 255, 255, 0.5) !important;
}

/* Responsive styles */
@media (max-width: 480px) {
    .u21-button {
        width: 100%;
    }
}
</style>