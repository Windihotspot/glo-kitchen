<template>
  <HeaderView></HeaderView>
  <div class="bg-gradient-to-r from-red-100 via-red-200 to-red-100 min-h-screen">
    <!-- Navbar -->
    

    <!-- Hero Section -->
    <section data-aos="fade-up" class="max-w-7xl mx-auto text-center px-6 py-16 md:px-10 md:py-20">
      <div class="flex flex-col-reverse md:flex-row items-center justify-between gap-12">
        <!-- Left Text -->
        <div class="w-full md:w-1/2 text-left">
          <h1 class="text-3xl sm:text-4xl md:text-5xl font-extrabold leading-snug text-gray-900">
            All Fast Food is <br />
            Available at <span class="text-red-500">Glo Kitchen</span>
          </h1>

          <p class="mt-4 text-gray-600 text-base sm:text-lg">
            We Are Just A Click Away When You Crave For Delicious Fast Food
          </p>

          <div
            class="flex flex-col sm:flex-row gap-4 sm:gap-6 mt-8 md:justify-start md:items-start"
          >
            <a
              href="https://wa.me/353899890446?text=Hello%20I%20would%20like%20to%20book%20an%20order"
              target="_blank"
              class="block w-full sm:w-auto"
            >
              <v-btn color="red" class="text-white py-3 w-full sm:w-auto" rounded="xl" size="large">
                Buy Now
              </v-btn>
            </a>
          </div>
        </div>

        <!-- Right Video -->
        <div class="w-full md:w-1/2">
          <video
            class="w-full max-w-md md:max-w-lg mx-auto rounded-md shadow-md"
            autoplay
            muted
            loop
            playsinline
          >
            <source
              src="https://cdn.pixabay.com/video/2017/08/30/11691-231758938_tiny.mp4"
              type="video/mp4"
            />
            Your browser does not support the video tag.
          </video>
        </div>
      </div>
    </section>

    <!-- Features Section -->

    <div data-aos="fade-right" class="max-w-7xl mx-auto px-4">
      <div class="grid gap-8 md:grid-cols-3">
        <div
          v-for="(feature, index) in benefits"
          :key="index"
          class="bg-white shadow-lg rounded-lg p-4 text-center transition hover:shadow-xl"
        >
          <div class="flex justify-center mb-2">
            <div class="w-8 h-8 flex items-center justify-center">
              <i :class="feature.icon" class="text-red-500 text-xl"></i>
            </div>
          </div>
          <h3 class="text-md font-semibold text-gray-800 mb-2">
            {{ feature.title }}
          </h3>
          <p class="text-gray-600 text-sm leading-relaxed">
            {{ feature.description }}
          </p>
        </div>
      </div>
    </div>

    <!-- Food cards -->
    <section class="max-w-7xl mx-auto px-2 sm:px-6 lg:px-8 py-10">
      <div
        class="px-4 sm:px-6 lg:px-12 py-6 sm:py-8 lg:py-12 flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4"
      >
        <!-- Text Section -->
        <div class="flex-1">
          <h2 class="text-2xl sm:text-3xl lg:text-4xl font-bold text-gray-900">
            Our <span class="text-red-500">Regular</span> Menu
          </h2>
          <p class="text-gray-500 mt-2 text-sm sm:text-base">
            These Are Our Regular Menus. You Can Order Anything You Like.
          </p>
        </div>

        <!-- Button Section -->
        <!-- <v-btn
          color="red"
          class="text-white px-6 py-3 w-full sm:w-auto"
          rounded="xl"
          size="large"
          variant="text"
        >
          View all
        </v-btn> -->
      </div>

      <div data-aos="fade-left" class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 p-2">
        <FoodCard
          v-for="product in allProducts"
          :key="product.id"
          :name="product.name"
          :image="product.image"
          :rating="product.rating"
          :reviews="product.reviews"
          :largePrice="product.price ? product.currency + ' ' + product.price.toFixed(2) : null"
          :smallPrice="
            product.smallPrice ? product.currency + ' ' + product.smallPrice.toFixed(2) : null
          "
          @buy="addToCart(product)"
        />
      </div>
    </section>

    <!-- Footer -->
    <FooterView></FooterView>
  </div>
</template>

<script setup>
import FoodCard from '@/components/FoodCard.vue'
import HeaderView from '@/components/HeaderView.vue'
import FooterView from '@/components/FooterView.vue'
import products from '@/data/products.json'

// Example usage
const allProducts = products
const benefits = [
  {
    title: 'Fast Delivery',
    description:
      'The food will be delivered to your location within 0 - 40 minutes of your ordering.',
    icon: 'fa-solid fa-truck-fast'
  },
  {
    title: 'Fresh Food',
    description: 'We deliver fresh cooked food.',
    icon: 'fa-solid fa-arrows-rotate'
  },
  {
    title: 'Affordable Delivery',
    description: 'Your food delivery comes with a delivery fee.',
    icon: 'fa-solid fa-money-bill-wave'
  }
]
</script>

<style scoped>
.v-btn {
  text-transform: none;
}
</style>
