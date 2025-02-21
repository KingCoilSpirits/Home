<script setup lang="ts">
import {onMounted, ref, watch} from 'vue';
import { useRouter, useRoute } from 'vue-router';

type TableUrls = {
  [key: string]: string;
};

const route = useRoute();
const router = useRouter();
const showOptions = ref(false);
const tableNumber = ref('');

watch(
    () => route.params.table,
    (newTableNumber) => {
      tableNumber.value = getTableNumber(newTableNumber);
    }
);

const handleOrderClick = (restaurant: string, tableNumber: string) => {

  switch (restaurant) {
    case 'ogzaza':
      const ogUrl = `${ogBaseURL}${route.params.table}`;
      window.location.href = ogUrl;      break;
    case 'kingcoil':
      const kcUrl = tableUrls[String(route.params.table)];

      if (kcUrl) {
        window.location.href = kcUrl;
      } else {
        console.error('Invalid table number for King Coil');
      }
      break;
    default:
      console.error('Invalid restaurant selection');
  }
};
// WOW, what a great simple url toast uses
const ogBaseURL = 'https://order.toasttab.com/order-and-pay/og-zaza-st-paul-550-vandalia-st/'
// WTF is square's deal?!?!? what an annoying way to handle urls
const tableUrls: TableUrls = {
  "111": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e7x0juilbsnimqfj3148",
  "112": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e7x0kbzypm27h49j53e0",
  "113": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e7x0kqzknncijsfss9k8",
  "114": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e7x0l4nmi6drau3dd5rc",
  "115": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e7x0liqskd98tcr2a8h4",
  "116": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e7x0lvntcmp56e9p8eaw",
  "121": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e8pw6ix2huffeva5down",
  "122": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e8pw6us854epmposdlxz",
  "123": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e8pw705t6ndv83lo1emv",
  "124": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e8pw7522xb6o5n2n7g47",
  "125": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e8pw7al1fidip1ehawk7",
  "126": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e8pw7ff5fo4pddkqst3r",
  "131": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9g5cfj9ueclx1cfkodb",
  "132": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9g5ctoln0ce9666w6lb",
  "133": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9g5cz26ogxmu5ouxun3",
  "134": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9g5d41pizdl2lse99pb",
  "135": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9g5d8xz105gtbqyv5gf",
  "211": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9utguctgzw0mynkikei",
  "212": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9uth47ihdjljib4ovyi",
  "213": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889e9uth8mhb3np8pil40cq",
  "221": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ea68awrufejk8hdd07h5",
  "222": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ea68bglkcov5sukcixnd",
  "231": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eag902r4wmhnfnr61358",
  "232": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eag90emaiaqaqlrsa9t8",
  "233": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eag90jwm49k9cx0jz57w",
  "31": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazympqyhd6hd2aqxzyv",
  "32": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyn487egzmmlzs4wnr",
  "33": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazynai78himxh4i1lqv",
  "34": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyngax01ht4z7kz8lz",
  "35": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazynltwg95lx9owqq1j",
  "36": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazynr7haxxgi1ujrjh3",
  "37": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazynwivetno98dykw9j",
  "38": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyo1t7ayk6vbuzartj",
  "39": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyo72fqfuez9jjgpxz",
  "40": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyod1n0xwtkxzgrsrb",
  "41": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyqkrot1q9z9q6rivr",
  "42": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyqreojp9tsu0azcyf",
  "43": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyqxg13zw032g5e53r",
  "44": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyr303a558kq67zrrr",
  "45": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889eazyr8j2uab2zkbg0biv",
  "311": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ebikl2pssdpj48cdgbvb",
  "312": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ebiklr87zfoe9qx47nyv",
  "313": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ebikm2jxi799s9k5ydcn",
  "314": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ebikmd3hu7oqst9iv11z",
  "321": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ecdr5sgsydpkdm7d60sa",
  "322": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ecdr63p9abbsv49trhiy",
  "331": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ed0bpt0wlbt5j48kxoxr",
  "332": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ed0bq5jv0i8act3aarnj",
  "333": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ed0bqbuxwrkcggioe4xr",
  "341": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889ednxzxe8ponxf6fqvgt7",
  "342": "https://square.online/app/store/api/seat/2fbmzh:19dgeo6tu57r:12889edny0ofi6kbgqke2zu1n"
};
const handleEventClick = () => {
  window.location.href = 'https://www.kingcoilspirits.com/event-space'
};
function getTableNumber(table: string | string[]): string {
  return Array.isArray(table) ? table[0] : table || '';
}

setTimeout(() => {
  showOptions.value = true;
}, 2000);

</script>
<template>
  <div id="app">

  <div class="stripe-container px-0 py-0 mx-0 mt-20">
    <div class="stripe w-screen"></div>
    <div class="stripe w-screen"></div>
  </div>
  <div class="flex flex-center">
<div class="text-center">
  <!-- Welcome Animation -->
  <q-slide-transition>
    <div v-if="!showOptions" class="welcome-animation">
      <img
          src="@/assets/KingCoilLogoOrange.png"
          alt="King Coil Spirits Logo"
          class="logo"
      />
    </div>
  </q-slide-transition>

  <!-- Options After Animation -->
  <q-slide-transition>
    <div v-if="showOptions" class="options">
      <div class="flex flex-center">
        <div class="py-0 px-0 mx-0 my-0">
          <img
              src="@/assets/OrderFood.png"
              alt="Click to order OG ZaZa Pizza"
              class="px-0 py-0 mx-0 my-0 welcome-logo"
              @click="handleOrderClick('ogzaza', tableNumber)"
          />
          <img
              src="@/assets/OGZaZaLogo.png"
              alt="OG ZaZa Logo"
              class="logo raised-logo"
              @click="handleOrderClick('ogzaza', tableNumber)"
          />
          <q-tooltip
              anchor="center right"
              self="center middle"
          >Click to order OG ZaZa Pizza</q-tooltip>
        </div>

        <div>
          <img
              src="@/assets/orderCocktails.png"
              alt="Click to order a King Coil cocktail"
              class="px-0 py-0 welcome-logo"
              @click="handleOrderClick('kingcoil', tableNumber)"
          />
          <img
              src="@/assets/KingCoilLogoOrange.png"
              alt="King Coil Spirits Logo"
              class="KCLogo"
              @click="handleOrderClick('kingcoil', tableNumber)"
          />
          <q-tooltip
              anchor="center right"
              self="center middle"
          >Click to order King Coil Spirits</q-tooltip>
        </div>
      </div>
      <div>
        <img
            src="@/assets/EventSpace.png"
            alt="Book your event with us!"
            class="event-logo"
            @click="handleEventClick"
        />
        <q-tooltip
            anchor="center right"
            self="center middle"
        >Click to book your event with us!</q-tooltip>
      </div>
    </div>
  </q-slide-transition>
</div>
</div>
  <div class="stripe-container bottom-stripe px-0 py-0 mx-0 mt-20">
    <div class="stripe w-screen"></div>
    <div class="stripe w-screen"></div>
  </div>
  </div>
</template>

<style scoped>
.welcome-animation {
  animation: fadeIn 1s ease-in-out;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 16px;
}

@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.welcome-logo {
  max-width: 80%;
  height: auto;
  max-height: 100vh;
  background-color: transparent;
  display: block;
  margin: 0 auto;
  padding: 0;
}

.logo, .KCLogo {
  max-width: 80%;
  height: auto;
  background-color: transparent;
  display: block;
  margin: 0 auto;
  padding: 0;
}

.options > div {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 40px;
}

.options {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
}

@media (max-width: 600px) {
  .logo, .KCLogo {
    max-width: 80%;
    max-height: 80%;
  }
  .welcome-logo, .event-logo {
    max-width: 70%;
    max-height: 70%;
  }
  .stripe {
    min-width: 100%;
  }
  .stripe-container {
    min-width: 100%;
  }
}

.stripe {
  width: 100%;
  height: 50px;
  background-image: url('@/assets/pattern-stripe.png');
  background-repeat: repeat-x;
  background-size: contain;
  padding: 0;
  margin: 0;
}
.bottom-stripe {
  width: 100%;
}

.stripe-container {
  display: flex;
  justify-content: center;
  margin: 0;
  padding: 0;
  width: 100%;
}

.event-logo {
  max-width: 100%;
  height: auto;
  background-color: transparent;
  display: block;
  margin: 20px auto 20px;
}

html, body {
  background-color: #f0f0f0;
  margin: 0;
  padding: 0;
  height: 100%;
  width: 100%;
}

#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: space-between;

}

</style>
