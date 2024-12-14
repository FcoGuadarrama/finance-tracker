<script setup lang="ts">
import OptionsVertical from '@/components/shared/OptionsVertical.vue'
import { RouterLink } from 'vue-router'

const images = [
  '/storage/images/gallery-1.png',
  '/storage/images/gallery-2.png',
  '/storage/images/gallery-3.png',
  '/storage/images/gallery-4.png',
  '/storage/images/gallery-5.png',
  '/storage/images/gallery-6.png',
  '/storage/images/gallery-7.png',
  '/storage/images/gallery-8.png',
  '/storage/images/gallery-5.png',
  '/storage/images/gallery-6.png',
  '/storage/images/gallery-7.png',
  '/storage/images/gallery-8.png'
]
</script>

<template>
  <div class="box mb-6">
    <div class="flex justify-between items-center bb-dashed pb-6 mb-6">
      <p class="font-medium">Gallery</p>
      <OptionsVertical />
    </div>
    <div class="grid grid-cols-4 gap-3">
      <div v-for="(img, i) in images" :key="i" class="col-span-1">
        <img :src="img" :width="96" :height="96" class="rounded-lg w-full" alt="gallery img" />
      </div>
      <div class="col-span-4 mt-6">
        <RouterLink to="#" class="btn-outline"> See All Image </RouterLink>
      </div>
    </div>
  </div>
</template>
