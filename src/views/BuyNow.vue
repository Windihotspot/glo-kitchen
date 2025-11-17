<template>
  <div class="min-h-screen">

    <!-- Header -->
    <HeaderView />

    <!-- Main Content Area -->
    <div class="flex-1">

      
        <div class="mx-auto max-w-7xl items-center flex gap-4 px-4">
          <div class="flex-1">
            <v-text-field
              rounded
              v-model="address"
              label="Delivery Address"
              placeholder="Enter Your Full Address"
              variant="outlined"
              density="compact"
              hide-details
              class="address-input"
              color="red"
            >
              <template v-slot:append-inner>
         <v-icon color="red">
      <i class="fa-solid fa-map-marker-alt"></i>
    </v-icon>
              </template>
            </v-text-field>
          </div>

          <v-btn icon variant="text">
            <v-icon>
              <i class="fa-solid fa-cart-shopping text-red-500"></i>
            </v-icon>
          </v-btn>
        </div>
     

      <!-- Products Section -->
      <div class="mx-auto max-w-7xl px-4 m-4 py-6">
        <v-row>
          <v-col v-for="product in products" :key="product.id" cols="6">
            <v-card
              class="product-card rounded-xs overflow-hidden cursor-pointer"
              height="130"
              @click="selectproduct(product)"
              hover
            >
              <v-img :src="product.image" height="130" cover class="product-image">
                <div class="overlay-dark">
                  <h3 class="text-white font-bold text-xs text-center tracking-wide">
                    {{ product.name }}
                  </h3>
                </div>
              </v-img>
            </v-card>
          </v-col>
        </v-row>
      </div>

    </div>

    <!-- Footer always at bottom -->
    <FooterView />

  </div>
</template>


<script setup>
import HeaderView from '@/components/HeaderView.vue'
import FooterView from '@/components/FooterView.vue'
import { ref } from 'vue'
import productsData from '@/data/products.json'

const address = ref('')

// const categories = [
//   {
//     id: 1,
//     name: 'CHOW MEIN',
//     image: 'https://images.unsplash.com/photo-1585032226651-759b368d7246?w=400&h=300&fit=crop'
//   },
//   {
//     id: 2,
//     name: 'CHICKEN STEAK',
//     image: 'https://images.unsplash.com/photo-1432139555190-58524dae6a55?w=400&h=300&fit=crop'
//   },
//   {
//     id: 3,
//     name: 'KACCHI',
//     image: 'https://images.unsplash.com/photo-1563379091339-03b21ab4a4f8?w=400&h=300&fit=crop'
//   },
//   {
//     id: 4,
//     name: 'BURGER',
//     image: 'https://images.unsplash.com/photo-1568901346375-23c9450c58cd?w=400&h=300&fit=crop'
//   }
// ]

const products = ref(productsData)

const selectproduct = (product) => {
  console.log('Selected product:', product)
  // Add your product selection logic here
}

const addToCart = (product) => {
  console.log('Added to cart:', product)
  // Add your cart logic here
}
</script>

<style scoped>



.product-image {
  position: relative;
}

.overlay-dark {
  position: absolute;
  inset: 0;
  background: rgba(0, 0, 0, 0.4);
  display: flex;
  align-items: center;
  justify-content: center;
}

.product-card {
  border-radius: 8px;
  transition: box-shadow 0.2s;
}

.product-card:hover {
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
}

.space-y-4 > * + * {
  margin-top: 1rem;
}
</style>
