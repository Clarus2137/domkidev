<template>
   <header class="header">
      <v-container :fluid="true" class="pa-2 pa-xl-4">
         <v-row class="justify-space-between align-center">
            <v-col cols="auto" class="text-center header__logo logo">
               <header-logo />
            </v-col>
            <v-col cols="auto" class="text-center header__address">
               <header-address />
            </v-col>
            <v-col cols="auto" class="text-center header__contacts">
               <header-contacts />
            </v-col>
            <v-col cols="auto" class="text-center header__callback">
               <header-callback />
            </v-col>
         </v-row>
      </v-container>
   </header>
</template>

<script setup lang="ts">
import HeaderLogo from './HeaderLogo.vue'
import HeaderAddress from './HeaderAddress.vue'
import HeaderContacts from './HeaderContacts.vue'
import HeaderCallback from './HeaderCallback.vue'
</script>