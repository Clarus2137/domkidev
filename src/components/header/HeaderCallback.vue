<template>
   <div class="text-center">
      <v-btn color="green-darken-1">
         Oddzwonimy
         <v-dialog v-model="dialog" activator="parent" max-width="60%" min-width="300px">
            <v-card>
               <callback-form />
            </v-card>
         </v-dialog>
      </v-btn>
   </div>
</template>



<script lang="ts">
import { defineComponent } from 'vue'
import CallbackForm from '@/components/CallbackForm.vue'

export default defineComponent({
   name: 'HeaderCallback',
   components: {
      CallbackForm
   },
   data() {
      return {
         dialog: false,
      }
   }
});
</script>