<script setup lang="ts">
import Hero from '@/components/Hero.vue'
import Features from '@/components/Features.vue'
import ShopBySport from '@/components/ShopBySport.vue'
import ShopByTrend from '@/components/ShopByTrend.vue'
import Membership from '@/components/Membership.vue'
</script>

<template>
  <main>
    <Hero />
    <Features />
    <ShopBySport />
    <ShopByTrend />
    <Membership 
      @join-click="handleJoinClick"
      @signin-click="handleSignInClick"
    />
  </main>
</template>

<script lang="ts">
function handleJoinClick() {
  console.log('Join button clicked')
  // Add your join logic here
}

function handleSignInClick() {
  console.log('Sign in button clicked')
  // Add your sign in logic here
}
</script>
