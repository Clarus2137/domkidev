<template>
   <v-form v-model="valid">
      <v-container>
         <v-row>
            <v-col cols="12" md="4">
               <v-text-field v-model="firstname" :rules="nameRules" :counter="50" label="Imię" required />
            </v-col>

            <v-col cols="12" md="4">
               <v-text-field v-model="email" :rules="emailRules" label="E-mail" required />
            </v-col>

            <v-col cols="12" md="4">
               <v-text-field v-model="phone" :rules="phoneRules" label="Telefon" required />
            </v-col>
         </v-row>
         <v-row class="justify-center">
            <v-col cols="auto">
               <v-btn type="submit" block>Wyślij</v-btn>
            </v-col>
         </v-row>
      </v-container>
   </v-form>
</template>



<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
   name: 'CallbackForm',
   data: () => ({
      valid: false,

      firstname: '',
      nameRules: [
         (value: string | undefined) => {
            if (value) {
               if (/\d/.test(value)) return 'Tylko litery'
               if (value.length <= 50) return true
               return 'To pole musi zawierać mniej niż 50 znaków'
            }
            return 'Wymagane'
         },
      ],

      email: '',
      emailRules: [
         (value: string | undefined) => {
            if (value) {
               if (/.+@.+\..+/.test(value)) return true
               return 'Adres e-mail musi być poprawny'
            } return 'Wymagane'
         }
      ],

      phone: '',
      phoneRules: [
         (value: string | undefined) => {
            if (value) {
               if (!/^[\d+]+$/.test(value)) return 'Nieprawidłowy format'
               return true
            } return 'Wymagane'
         }
      ],
   }),
})
</script>