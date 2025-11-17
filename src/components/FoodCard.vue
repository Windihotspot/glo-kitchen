<template>
  <div
    class="bg-white rounded-lg shadow-lg p-4 py-10 flex flex-col items-center text-center transition hover:shadow-md"
  >
    <!-- Food Image -->
    <div class="rounded-full border-3 border-red-400 w-28 h-28 overflow-hidden mb-3">
      <v-img :src="image" cover class="rounded-full w-full h-full" />
    </div>

    <!-- Name -->
    <h3 class="font-semibold text-lg">{{ name }}</h3>

    <!-- Rating -->
    <div class="flex items-center justify-center mt-1 gap-1">
      <span v-for="star in 5" :key="star" class="text-yellow-400">
        <v-icon size="18" class="fa-solid fa-star text-yellow-500"></v-icon>
      </span>

      <span class="text-sm text-gray-500">({{ reviews }})</span>
    </div>

    <!-- Price -->
    <div class="price mt-2 text-sm">
      <!-- Case 1: Only one price (largePrice), show price only -->
      <div v-if="largePrice && !smallPrice">
        {{ largePrice }}
      </div>

      <!-- Case 2: Both prices exist -->
     <div v-if="largePrice && smallPrice">
  Large size - {{ largePrice }} | Small size - {{ smallPrice }}
</div>


    </div>

    <!-- Buy Button -->
    <v-btn class="mt-3 rounded-full text-white" color="red" size="small" @click="$emit('buy')">
      Buy Now
    </v-btn>
  </div>
</template>

<script setup>
defineProps({
  name: { type: String, required: true },
  image: { type: String, required: true },
  rating: { type: Number, default: 5 },
  reviews: { type: Number, default: 0 },
  largePrice: { type: String, default: null },
  smallPrice: { type: String, default: null }
})
defineEmits(['buy'])
</script>

<style scoped>
.v-btn {
  text-transform: none;
}
</style>
