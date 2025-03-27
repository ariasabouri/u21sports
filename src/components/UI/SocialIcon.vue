<template>
    <a :href="href" :class="['social-icon', size]" :title="network" @click="handleClick">
        <img :src="getIconSrc()" :alt="network">
    </a>
</template>

<script setup lang="ts">
import { computed } from 'vue';

// Import all social icons
import facebookIcon from '@/assets/icons/ph-facebook-logo.svg';
import twitterIcon from '@/assets/icons/ph-twitter-logo.svg';
import instagramIcon from '@/assets/icons/ph-instagram-logo.svg';
import youtubeIcon from '@/assets/icons/ph-youtube-logo.svg';

const emit = defineEmits<{
    (e: 'click', network: string): void;
}>();

const props = withDefaults(defineProps<{
    network: 'facebook' | 'twitter' | 'instagram' | 'youtube';
    href?: string;
    size?: 'small' | 'medium' | 'large';
}>(), {
    href: '#',
    size: 'medium'
});

// Get appropriate icon based on network
const getIconSrc = () => {
    switch (props.network) {
        case 'facebook':
            return facebookIcon;
        case 'twitter':
            return twitterIcon;
        case 'instagram':
            return instagramIcon;
        case 'youtube':
            return youtubeIcon;
        default:
            return '';
    }
};

// Handle click event
const handleClick = (event: Event) => {
    if (props.href === '#') {
        event.preventDefault();
    }
    emit('click', props.network);
};
</script>

<style scoped>
.social-icon {
    display: flex;
    align-items: center;
    justify-content: center;
    border-radius: 50%;
    background-color: var(--color-background-soft);
    transition: all 0.2s ease;
    cursor: pointer;
}

.social-icon:hover {
    background-color: var(--color-primary);
    transform: scale(1.1);
}

.small {
    width: 30px;
    height: 30px;
}

.small img {
    width: 15px;
    height: 15px;
}

.medium {
    width: 40px;
    height: 40px;
}

.medium img {
    width: 24px;
    height: 24px;
}

.large {
    width: 50px;
    height: 50px;
}

.large img {
    width: 30px;
    height: 30px;
}
</style>