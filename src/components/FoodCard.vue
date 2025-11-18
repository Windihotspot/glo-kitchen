<template>
  <div
    class="bg-white rounded-lg shadow-lg p-4 py-10 flex flex-col items-center text-center transition hover:shadow-md"
  >
    <!-- Food Image -->
    <div class="rounded-full border-3 border-red-400 w-28 h-28 overflow-hidden mb-3">
      <v-img :src="props.image" cover class="rounded-full w-full h-full" />
    </div>

    <!-- Name -->
    <h3 class="font-semibold text-lg">{{ props.name }}</h3>

    <!-- Rating -->
    <div class="flex items-center justify-center mt-1 gap-1">
      <span v-for="star in 5" :key="star" class="text-yellow-400">
        <v-icon size="18" class="fa-solid fa-star text-yellow-500"></v-icon>
      </span>

      <span class="text-sm text-gray-500">({{ props.reviews }})</span>
    </div>

    <!-- Price -->
    <div class="price mt-2 text-sm">
      <div v-if="props.largePrice && !props.smallPrice">
        {{ props.largePrice }}
      </div>

      <div v-if="props.largePrice && props.smallPrice">
        Large size - {{ props.largePrice }} | Small size - {{ props.smallPrice }}
      </div>
    </div>

    <!-- Buy Button -->
    <v-btn class="mt-3 rounded-full text-white" color="red" size="small" @click="orderNow">
      Buy Now
    </v-btn>
  </div>
</template>

<script setup>
/* FIXED — store props into a variable */
const props = defineProps({
  name: { type: String, required: true },
  image: { type: String, required: true },
  rating: { type: Number, default: 5 },
  reviews: { type: Number, default: 0 },
  largePrice: { type: String, default: null },
  smallPrice: { type: String, default: null }
})

const whatsappNumber = "353899890446"

const orderNow = () => {
  let priceMessage = ""

  if (props.largePrice && props.smallPrice) {
    priceMessage = `Large: ${props.largePrice} | Small: ${props.smallPrice}`
  } else if (props.largePrice) {
    priceMessage = `Price: ${props.largePrice}`
  } else {
    priceMessage = "Price not listed"
  }

  const message = `Hello, I would like to place an order.\n\nItem: ${props.name}\n${priceMessage}\n\nPlease confirm availability. 😊`

  const link = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`

  window.open(link, "_blank")
}
</script>

<style scoped>
.v-btn {
  text-transform: none;
}
</style>
