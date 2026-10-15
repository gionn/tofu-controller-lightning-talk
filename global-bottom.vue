<script setup lang="ts">
import { useNav } from '@slidev/client'

const { currentSlideNo } = useNav()
</script>

<template>
  <div v-if="currentSlideNo > 1" class="fixed top-4 right-4 text-sm opacity-50 z-10">
    {{ currentSlideNo }}
  </div>
</template>
