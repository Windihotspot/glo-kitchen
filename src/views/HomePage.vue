<template>
  <div class="bg-gradient-to-r from-red-100 via-red-200 to-red-100 min-h-screen">
    <!-- Navbar -->
    <HeaderView></HeaderView>

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
            <v-btn color="red" class="text-white px-6 py-3 w-auto" rounded="xl" size="large">
              Buy Now
            </v-btn>
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

    <div data-aos="fade-right" :data-aos-delay="index * 100" class="max-w-7xl mx-auto px-4">
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

      <div
        data-aos="fade-left"
        :data-aos-delay="index * 100"
        class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 p-2"
      >
        <FoodCard
          name="Coke and fanta"
          price="€2.20"
          image="https://toppng.com/uploads/preview/fanta-food-png-free-11667343744aaeokoh60g.png"
          rating="5"
          reviews="112"
          @buy="addToCart"
        />
        <FoodCard
          name="Bottle Water"
          price="€1.90"
          image="https://images.openfoodfacts.org/images/products/539/154/524/0026/front_en.3.full.jpg"
          rating="5"
          reviews="142"
          @buy="addToCart"
        />

        <FoodCard
          name="Jollof rice and chicken or beef"
          price="€12.00"
          image="https://images.unsplash.com/photo-1603496987674-79600a000f55?fm=jpg&q=60&w=3000&ixlib=rb-4.1.0&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8Y2hpY2tlbiUyMHJpY2V8ZW58MHx8MHx8fDA%3D"
          rating="4"
          reviews="123"
        />

        <FoodCard
          name="Chicken curry sauce and white rice"
          price="€10.00 for Large size | €7.00 for Small size"
          image="https://cdn.pixabay.com/photo/2023/06/02/19/36/ai-generated-8036274_1280.png"
          rating="5"
          reviews="152"
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
const benefits = [
  {
    title: 'Fast Delivery',
    description: 'The food will be delivered to your home within 0 - 40 minutes of your ordering.',
    icon: 'fa-solid fa-truck-fast'
  },
  {
    title: 'Fresh Food',
    description:
      'Your food will be delivered 100% fresh to your home. We do not deliver stale food.',
    icon: 'fa-solid fa-arrows-rotate'
  },
  {
    title: 'Free Delivery',
    description: 'Your food delivery comes with a delivery fee.',
    icon: 'fa-solid fa-mobile-screen-button'
  }
]
</script>

<style scoped>
.v-btn {
  text-transform: none;
}
</style>
