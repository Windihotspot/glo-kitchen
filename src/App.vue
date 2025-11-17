<script setup lang="ts">
import { RouterView } from 'vue-router'
</script>

<template>
  <main class="min-h-screen text-neutral-800 bg-gradient-to-r from-red-100 via-red-200 to-red-100">
    <RouterView />
  </main>
</template>

<style>
.custom-btn {
  background-color: #27bfa0;
}
.v-application {
  font-family: 'Sora', sans-serif;
}
</style>
