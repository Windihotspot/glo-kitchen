<template>
  <header
    class="mx-auto max-w-7xl text-black flex items-center justify-between px-8 py-4 relative bg-gradient-to-r from-red-100 via-red-200 to-red-100"
   
  >
    <!-- Logo -->
  <div class="flex items-center space-x-2">
  <img src="../assets/glo-kitchen.jpg" alt="Glo kitchen Logo" class="w-10 h-10 rounded-full" />

  <!-- Text stacked vertically -->
  <div class="flex flex-col leading-tight">
    <span class="font-semibold text-black text-lg">Glo Kitchen</span>
    <span class="font-light text-black text-sm -mt-1">Intercontinental takeaway food</span>
  </div>
</div>


    <!-- Desktop Nav -->
    <nav class="hidden lg:flex items-center space-x-8 text-black font-medium">
      <router-link to="/" class="nav-link">Home</router-link>
      <router-link to="/" class="nav-link">Services</router-link>
      <router-link to="/" class="nav-link">About Us</router-link>
      <router-link to="/" class="nav-link">Contact</router-link>
    </nav>

    <!-- Desktop Buttons -->
    <v-btn
      to="/"
      size="small"
      rounded="lg"
      class="!hidden lg:!inline-flex !px-6 !bg-red-500 hover:!bg-red-600 text-white"
    >
      Book an Order
    </v-btn>

    

    <!-- Mobile Hamburger -->
    <button class="lg:hidden text-black" @click="showMenu = !showMenu">
      <svg
        v-if="!showMenu"
        xmlns="http://www.w3.org/2000/svg"
        class="w-6 h-6"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
      >
        <path stroke-linecap="round" stroke-linejoin="round" d="M4 6h16M4 12h16M4 18h16" />
      </svg>

      <svg
        v-else
        xmlns="http://www.w3.org/2000/svg"
        class="w-6 h-6"
        fill="none"
        stroke="currentColor"
        stroke-width="2"
      >
        <path stroke-linecap="round" stroke-linejoin="round" d="M6 18L18 6M6 6l12 12" />
      </svg>
    </button>

    <!-- Mobile Menu -->
    <div
    data-aos="fade-down"
    :data-aos-delay="index * 100"
      v-if="showMenu"
      class="absolute m-2 top-full left-0 w-full bg-white border-t shadow-md lg:hidden z-50"
    >
      <nav class="flex flex-col space-y-4 p-4 text-gray-800 font-medium">

        <router-link to="/"  class="mobile-link">Home</router-link>
        <router-link to="/"  class="mobile-link">Services</router-link>
        <router-link to="/"  class="mobile-link">About us</router-link>
        <router-link to="/"  class="mobile-link">Contact</router-link>

        <v-btn
          size="large"
          rounded="lg"
          class="!bg-red-500 hover:!bg-red-600 text-white px-6"
          @click="showMenu = false"
        >
           Book an order
        </v-btn>

    

      </nav>
    </div>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from 'vue'
import { RouterLink } from 'vue-router'

const showDropdown = ref(false)
const showMobileDropdown = ref(false)
const showMenu = ref(false)

const services = [
  { title: 'Bank Statement Analysis', description: 'Advanced bank statement analysis solutions', path: '/BankStatementAnalysis' },
  { title: 'Loan Origination', description: 'Advanced loan origination solutions', path: '/coreservices#loan-origination' },
  { title: 'Credit Underwriting', description: 'Advanced credit underwriting solutions', path: '/coreservices#credit-underwriting' },
  { title: 'ID & Credit Search', description: 'Advanced id & credit search solutions', path: '/coreservices#id-credit-search' },
  { title: 'Custom Scorecard', description: 'Advanced custom scorecard solutions', path: '/coreservices#custom-scorecard' }
]

const dropdownRef = ref(null)

function toggleDropdown() {
  showDropdown.value = !showDropdown.value
}

function handleClickOutside(event) {
  if (dropdownRef.value && !dropdownRef.value.contains(event.target)) {
    showDropdown.value = false
  }
}

onMounted(() => document.addEventListener('click', handleClickOutside))
onBeforeUnmount(() => document.removeEventListener('click', handleClickOutside))
</script>

<style scoped>
/* Desktop nav link styles */
.nav-link {
  padding: 0.5rem 1rem;
  transition: 0.2s;
}
.nav-link:hover {
  background-color: rgba(255, 255, 255, 0.2);
  border-radius: 6px;
}

/* Mobile nav link */
.mobile-link {
  padding: 0.5rem 0;
  color: #eb702b;
}

.v-btn {
  text-transform: none;
}
</style>
