<script setup lang="ts">
import Hero from '@/components/Hero.vue'
import Features from '@/components/Features.vue'
import TrainingTypes from '@/components/TrainingTypes.vue'
import GridSection from '@/components/GridSection.vue'
import Membership from '@/components/Membership.vue'
</script>

<template>
  <main>
    <Hero />
    <Features />

    <!-- Use TrainingTypes component -->
    <TrainingTypes title="Unsere Trainingsarten" :items="trainingTypes" ctaText="Mehr erfahren"
      @item-click="handleTrainingClick" />

    <!-- Use GridSection for age groups -->
    <GridSection title="Altersgruppen" :gridItems="ageGroups" ctaText="Details" :columns="3" minWidth="250px"
      aspectRatio="4/3" @item-click="handleAgeGroupClick" />

    <Membership @join-click="handleJoinClick" @signin-click="handleSignInClick" />
  </main>
</template>

<script lang="ts">
// Training types data
const trainingTypes = [
  {
    title: 'Fußballtraining',
    description: 'Technik, Taktik und Spielpraxis für alle Niveaus.',
    image: '/src/assets/images/img_kagan_1.jpeg'
  },
  {
    title: 'Athletiktraining',
    description: 'Kraft, Ausdauer und Koordination für bessere Leistung.',
    image: '/src/assets/images/img_kagan_2.jpeg'
  },
  {
    title: 'Kombi-Training',
    description: 'Die perfekte Verbindung aus Fußball und Athletik.',
    image: '/src/assets/images/stock/anthomkii_imagine_a_studio_photoshoot_of_professional_athletes__23f93872-3b1c-4f23-845c-ea25f1e1fb63 1.png'
  }
]

// Age groups data with Kagan images
const ageGroups = [
  {
    title: 'U10-U11',
    description: 'Grundlegende Techniken und Spielverständnis',
    image: '/src/assets/images/img_kagan_1.jpeg'
  },
  {
    title: 'U12-U13',
    description: 'Aufbauendes Training mit Taktik',
    image: '/src/assets/images/img_kagan_2.jpeg'
  },
  {
    title: 'U14-U15',
    description: 'Fortgeschrittenes Training',
    image: '/src/assets/images/img_kagan_1.jpeg'
  }
]

// Event handlers
function handleTrainingClick(index: number) {
  console.log('Training type clicked:', trainingTypes[index])
}

function handleAgeGroupClick(index: number) {
  console.log('Age group clicked:', ageGroups[index])
}

function handleJoinClick() {
  console.log('Join button clicked')
}

function handleSignInClick() {
  console.log('Sign in button clicked')
}
</script>
