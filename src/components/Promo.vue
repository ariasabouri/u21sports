<template>
    <div class="promo" v-if="isVisible">
        <p class="text-wrapper">{{ promoText }}</p>
        <div class="div"><router-link :to="ctaLink">{{ ctaLinkText }}</router-link></div>
        <button class="close-button" @click="hidePromo" aria-label="Close">×</button>
    </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const isVisible = ref(true);

const hidePromo = () => {
    isVisible.value = false;
};

const props = withDefaults(defineProps<{
    // Content
    promoText?: string,
    ctaLinkText?: string,
    ctaLink?: string,
}>(), {
    promoText: 'Jetzt anmelden und 10% Rabatt auf dein erstes Training sichern!',
    ctaLinkText: 'Hier klicken',
    ctaLink: '/training',
})
</script>

<style>
.promo {
    align-items: center;
    background-color: #449596;
    display: flex;
    flex-direction: column;
    gap: 5px;
    justify-content: center;
    padding: 10px;
    position: relative;
}

.promo .text-wrapper {
    color: #ffffff;
    font-family: "Roboto-Regular", Helvetica;
    font-size: 12px;
    font-weight: 400;
    letter-spacing: 0;
    line-height: normal;
    margin-top: -1.00px;
    position: relative;
    white-space: nowrap;
    width: fit-content;
}

.promo .div {
    color: #ffffff;
    font-family: "Roboto-Regular", Helvetica;
    font-size: 10px;
    font-weight: 400;
    letter-spacing: 0;
    line-height: normal;
    position: relative;
    text-decoration: underline;
    white-space: nowrap;
    width: fit-content;
}

.close-button {
    position: absolute;
    top: 5px;
    right: 10px;
    background: none;
    border: none;
    color: #ffffff;
    font-size: 18px;
    cursor: pointer;
    padding: 0;
    height: 20px;
    width: 20px;
    display: flex;
    align-items: center;
    justify-content: center;
    opacity: 0.7;
    transition: opacity 0.2s;
}

.close-button:hover {
    opacity: 1;
}
</style>