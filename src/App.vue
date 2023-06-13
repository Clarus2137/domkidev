<template>
   <v-app>
      <v-header />
      <v-main>
         <v-slider />
         <v-presentation />
      </v-main>
   </v-app>
</template>

<script setup lang="ts">
import VHeader from '@/components/header/VHeader.vue'
import VSlider from '@/components/home/VSlider.vue'
import VPresentation from '@/components/home/VPresentation.vue';
</script>
