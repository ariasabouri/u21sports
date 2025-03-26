<template>
  <main>
    <Hero />
    <!--<Features />-->

    <!-- Use TrainingTypes component -->
    <TrainingTypes title="Unsere Trainingsarten" :items="trainingTypes" ctaText="Mehr erfahren"
      @item-click="handleTrainingClick" />

    <!-- Use GridSection for age groups -->
    <GridSection title="Altersgruppen" :gridItems="ageGroups" ctaText="Details" :columns="3" minWidth="250px"
      aspectRatio="4/3" @item-click="handleAgeGroupClick" />

    <Membership @join-click="handleJoinClick" @signin-click="handleSignInClick" />
  </main>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router';
import Hero from '@/components/Hero.vue'
import Features from '@/components/Features.vue'
import TrainingTypes from '@/components/TrainingTypes.vue'
import GridSection from '@/components/GridSection.vue'
import Membership from '@/components/Membership.vue'

// Setup router
const router = useRouter();

// Import images
import kaganImg1 from '@/assets/images/img_kagan_1.jpeg'
import kaganImg2 from '@/assets/images/img_kagan_2.jpeg'
import athletesImg from '@/assets/images/stock/anthomkii_imagine_a_studio_photoshoot_of_professional_athletes__23f93872-3b1c-4f23-845c-ea25f1e1fb63 1.png'

// Training types data
const trainingTypes = [
  {
    title: 'Fußballtraining',
    description: 'Technik, Taktik und Spielpraxis für alle Niveaus.',
    image: kaganImg1
  },
  {
    title: 'Athletiktraining',
    description: 'Kraft, Ausdauer und Koordination für bessere Leistung.',
    image: kaganImg2
  },
  {
    title: 'Kombi-Training',
    description: 'Die perfekte Verbindung aus Fußball und Athletik.',
    image: athletesImg
  }
]

// Age groups data
const ageGroups = [
  {
    title: 'U10-U11',
    description: 'Grundlegende Techniken und Spielverständnis',
    image: kaganImg1
  },
  {
    title: 'U12-U13',
    description: 'Aufbauendes Training mit Taktik',
    image: kaganImg2
  },
  {
    title: 'U14-U15',
    description: 'Fortgeschrittenes Training',
    image: kaganImg1
  }
]

// Event handlers
function handleTrainingClick(index: number) {
  // Navigate to TrainingView
  router.push('/training');
}

function handleAgeGroupClick(index: number) {
  // Navigate to AgeGroupsView
  router.push('/age-groups');
}

function handleJoinClick() {
  console.log('Join button clicked')
}

function handleSignInClick() {
  console.log('Sign in button clicked')
}
</script>
