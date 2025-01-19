<script setup lang="ts">
import {onMounted, ref} from 'vue';
import { useRouter, useRoute } from 'vue-router';

const route = useRoute();
const router = useRouter();
const showOptions = ref(false);
const tableNumber = ref('');


onMounted(() => {
  if (route.params.table) {
    console.log("Table number:", route.params.table);
  } else {
    console.log("No table number provided");
  }
});
// Simulate a welcome animation and then show options
setTimeout(() => {
  showOptions.value = true;
}, 2000);

</script>
<template class="h-screen">
  <div class="stripe-container">
    <div class="stripe w-screen"></div> <!-- Add this div for the stripe -->
    <div class="stripe w-screen"></div> <!-- Add this div for the stripe -->
  </div>
  <div class="q-pa-md flex flex-center h-screen">
<div class="text-center">
  <!-- Welcome Animation -->
  <q-slide-transition>
    <div v-if="!showOptions" class="welcome-animation">
      <img
          src="@/assets/KingCoilLogoOrange.png"
          alt="King Coil Spirits Logo"
          class="q-my-md"
      />      <h1 class="text-h4 text-bold">Welcome to King Coil Spirits!</h1>
    </div>
  </q-slide-transition>

  <!-- Options After Animation -->
  <q-slide-transition>
    <div v-if="showOptions" class="options h-screen">
      <h2 class="text-h5 q-my-md">What are you in the mood for?</h2>
      <div>
        <p v-if="route.params.table">Table Number: {{ route.params.table }}</p>
      </div>
      <div class="q-mt-lg">
        <div>
          <img
              src="@/assets/OGZaZaLogo.png"
              alt="OG ZaZa Logo"
              class="logo raised-logo"
              @click="router.push('/pizza')"
          />
          <q-tooltip
              anchor="center right"
              self="center middle"
          >Click to order OG ZaZa Pizza</q-tooltip>
        </div>

        <div>
          <img
              src="@/assets/KingCoilLogoOrange.png"
              alt="King Coil Spirits Logo"
              class="KCLogo raised-image"
              @click="router.push('/cocktails')"
          />
          <q-tooltip
              anchor="center right"
              self="center middle"
          >Click to order King Coil Spirits</q-tooltip>
        </div>
      </div>
    </div>
  </q-slide-transition>
</div>
</div>
</template>

<style scoped>
.welcome-animation {
  animation: fadeIn 3s ease-in-out;
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.logo {
  max-width: 150px; /* Adjust this value for desired size */
  max-height: 150px;
  width: auto;
  height: auto;
  background-color: transparent;
  display: block; /* Ensures proper centering */
  margin: auto; /* Centers logos inside buttons */
}
.KCLogo {
  max-width: 300px;
  width: auto;
  height: auto;
  background-color: white;
  display: block; /* Ensures proper centering */
  margin: auto; /* Centers logos inside buttons */
  padding: 10px;
  border-radius: 2%;
}
.stripe {
  width: 100%;
  height: 50px; /* Adjust the height as needed */
  background-image: url('@/assets/pattern-stripe.png');
  background-repeat: repeat-x;
  background-size: contain;
}
.raised-image {
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1), 0 1px 3px rgba(0, 0, 0, 0.08);
  transition: box-shadow 0.3s ease-in-out;
}
.raised-image:hover {
  box-shadow: 0 10px 15px rgba(0, 0, 0, 0.1), 0 4px 6px rgba(0, 0, 0, 0.08);
}
.stripe-container {
  display: flex;
  justify-content: center;
}
</style>
