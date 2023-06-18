<template>
   <v-app>
      <v-header />
      <v-main>
         <router-view />
      </v-main>
   </v-app>
</template>

<script setup lang="ts">
import VHeader from '@/components/header/VHeader.vue'
</script>
