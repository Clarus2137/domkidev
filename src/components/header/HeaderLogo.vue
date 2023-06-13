<template>
   <a href="https://vuejs.org/" target="_blank">
      <img src="./../../assets/img/logo.png" class="logo__img" width="150" alt="Domki logo" />
   </a>
</template>

<script setup lang="ts">

</script>

<style scoped lang="scss">
.logo__img {
   will-change: filter;
   transition: filter 300ms;

   &:hover {
      filter: drop-shadow(0 0 2em #646cffaa);
   }
}
</style>