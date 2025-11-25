<script setup lang="ts">
import { ref, onMounted } from 'vue'

const showTooltip = ref(false)

onMounted(() => {
  // show tooltip immediately on first load
  showTooltip.value = true

  // repeat every 2 minutes
  setInterval(() => {
    showTooltip.value = true

    // hide after 4 seconds
    setTimeout(() => {
      showTooltip.value = false
    }, 4000)
  }, 120000) // 120000ms = 2 minutes
})
</script>

<template>
  <main class="min-h-screen text-neutral-800">
    <RouterView />

    <!-- Tooltip -->
    <div
      v-if="showTooltip"
      class="fixed bottom-20 right-5 bg-white text-black px-3 py-2 rounded shadow-lg text-sm fade-tooltip z-50"
    >
      Book an order
    </div>

    <!-- WhatsApp Floating Button -->
    <a href="https://wa.me/353899890446" target="_blank" class="fixed bottom-5 right-5">
      <img src="/icons8-whatsapp-48.png" alt="">
    </a>
  </main>
</template>

<style>
/* Tooltip fade animation */
.fade-tooltip {
  animation: fadeInOut 4s ease-in-out;
}

@keyframes fadeInOut {
  0% {
    opacity: 0;
    transform: translateY(10px);
  }
  10% {
    opacity: 1;
    transform: translateY(0);
  }
  90% {
    opacity: 1;
    transform: translateY(0);
  }
  100% {
    opacity: 0;
    transform: translateY(10px);
  }
}

/* Floating WhatsApp button animation */
@keyframes float {
  0% {
    transform: translateY(0);
  }
}

.animate-float {
  animation: float 2s infinite ease-in-out;
}
</style>
