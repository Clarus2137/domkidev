<template>
   <v-container :fluid="true" class="px-0 py-2 pa-xl-4">
      <v-row>
         <v-col>
            <v-carousel hide-delimiters show-arrows="hover" height="auto" cycle interval="5000">
               <v-carousel-item src="src/assets/img/domki-wiewiurki.png" contain></v-carousel-item>
               <v-carousel-item src="src/assets/img/domki-jezyki.png" contain></v-carousel-item>
            </v-carousel>
         </v-col>
      </v-row>
   </v-container>
</template>



<script lang="ts" setup>

</script>