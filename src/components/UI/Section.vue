<template>
    <section class="u21-section" :style="sectionStyle">
        <div class="section-header" v-if="$slots.header || title">
            <slot name="header">
                <h2 class="section-title">{{ title }}</h2>
            </slot>
            <slot name="header-actions"></slot>
        </div>

        <div class="section-content">
            <slot></slot>
        </div>

        <div class="section-footer" v-if="$slots.footer">
            <slot name="footer"></slot>
        </div>
    </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const props = withDefaults(defineProps<{
    title?: string;
    backgroundColor?: string;
    textColor?: string;
    padding?: string;
    maxWidth?: string;
}>(), {
    backgroundColor: 'var(--color-background)',
    textColor: 'var(--color-text)',
    padding: '40px 8%',
    maxWidth: '100%'
});

// Computed style for the section
const sectionStyle = computed(() => ({
    backgroundColor: props.backgroundColor,
    color: props.textColor,
    padding: props.padding
}));
</script>

<style scoped>
.u21-section {
    display: flex;
    flex-direction: column;
    gap: 30px;
    width: 100%;
    background-color: var(--color-background);
    color: var(--color-text);
}

.section-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
}

.section-title {
    font-family: "Roboto-Bold", Helvetica, sans-serif;
    font-size: 24px;
    font-weight: 700;
    color: var(--color-text);
}

.section-content {
    width: 100%;
    margin: 0 auto;
    max-width: v-bind('props.maxWidth');
}

.section-footer {
    width: 100%;
    margin-top: 20px;
}

@media (max-width: 1024px) {
    .u21-section {
        padding: 30px 5%;
    }
}

@media (max-width: 768px) {
    .section-title {
        font-size: 20px;
    }
}

@media (max-width: 480px) {
    .u21-section {
        padding: 20px 4%;
    }
}
</style>