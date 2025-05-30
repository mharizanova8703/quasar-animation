<template>
  <div>
    <div class="list-items">
      <div class="row q-gutter-md justify-center">
        <div
          v-for="(card, index) in cards"
          :key="index"
          class="col-11 col-sm-6 col-md-3 col-lg-3 flex justify-center"
        >
                  <q-card
            class="my-card q-mb-lg"
            @mouseenter="showSquirrel(index)"
            @mouseleave="hideSquirrel(index)"
          >
          <SquirrelSection :ref="el => squirrelRefs[index] = el?.squirrelRef ?? null" />
            <q-card-section class="text-center">
              <img ref="images" :src="card.img" class="card-image" />
              <div class="font-pxl text-center montserrat-bold">{{ card.title }}</div>
              <div class="text-subtitle2 text-center">{{ card.author }}</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
              {{ card.text.length > 50 ? card.text.substring(0, 50) + "..." : card.text }}
            </q-card-section>

            <q-btn label="Read More" color="yellow-orange q-mb-md btn-alert" @click="openModal(card)" />
          </q-card>
        </div>
      </div>
    </div>
    <q-dialog v-model="selectedCard.alert">
      <q-card class="model-card q-pa-md">
        <q-card-section class="text-center">
          <div class="montserrat-bold font-xls alert-btn mx-auto">{{ selectedCard.title }}</div>
        </q-card-section>

        <q-card-section class="q-pt-none text-center">
          <q-img ref="modalImage" :src="selectedCard.img" class="modal-image" />
          <p>{{ selectedCard.text }}</p> <!-- Full text displayed in modal -->
        </q-card-section>

        <q-card-actions align="right">
          <q-btn flat label="Close" color="yellow-orange q-my-auto" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
  
</template>

<script setup>
import { ref, onMounted } from "vue";
import SquirrelSection from "src/components/SquirrelSection.vue";

const loadGSAP = () => {
  return new Promise((resolve) => {
    if (window.gsap) return resolve(); // Prevents multiple loads
    const script = document.createElement("script");
    script.src = "https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js";
    script.onload = resolve;
    document.head.appendChild(script);
  });
};

const selectedCard = ref({ alert: false });
const images = ref([]);
const squirrelRefs = ref([]);
const modalImage = ref(null);
const showSquirrel = async (index) => {
  await loadGSAP();
  const squirrel = squirrelRefs.value[index];
  if (squirrel) {
    gsap.to(squirrel, {
      y: -50,
      opacity: 1,
      duration: 0.6,
      ease: "back.out(1.7)",
    });
  }
};

const hideSquirrel = async (index) => {
  await loadGSAP();
  const squirrel = squirrelRefs.value[index];
  if (squirrel) {
    gsap.to(squirrel, {
      y: 0,
      opacity: 0,
      duration: 0.6,
      ease: "power2.inOut",
    });
  }
};

const cards = ref([
  {
    title: "Menu Plan",
    text:
      "A well-planned camping menu keeps you energized for outdoor activities. Pack easy-to-cook meals like foil-wrapped veggies, grilled meats, pasta, and one-pot meals. Don’t forget high-energy snacks and hydration!",
    img: "food.png",
    alert: false,
  },
  {
    title: "Snacks",
    text:
      "Quick snacks are a must for camping. Pack protein bars, nuts, dried fruits, jerky, and s’mores ingredients. Bring some easy-to-carry trail mix for energy boosts during hikes!",
    img: "snack.png",
    alert: false,
  },
  {
    title: "Drinking Water",
    text: "Make sure you bring enough drinking water or a water filter.",
    img: "water.png",
    alert: false,
  },
]);

const openModal = (card) => {
  selectedCard.value = { ...card, alert: true };

  setTimeout(() => {
    gsap.from(modalImage.value.$el, {
      opacity: 0,
      scale: 0.5,
      duration: 0.8,
      ease: "power2.out"
    });
  }, 100);
};

onMounted(async () => {
  await loadGSAP();

  gsap.from(images.value.map(img => img.$el), {
    opacity: 0,
    scale: 0.9,
    duration: 1.2,
    stagger: 0.3,
    ease: "power3.out"
  });
});
</script>

<style scoped lang="scss">
.list-items {
  width: 100%;
  padding: 3rem 0rem;
  z-index: 1;
}
.my-card {
  position: relative;
  overflow: visible;
  background: $background;
  padding: 4rem 2rem;
  border-radius: 10px;
  box-shadow: 0 2px 12px rgba(0,0,0,0.1);
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
  min-height: 300px; 
  width: 100%;
  color:$white;
}
.q-dialog__backdrop {
    z-index: -1;
    pointer-events: all;
    outline: 0;
    background: rgba(0, 0, 0, 0.99);
}
.q-card__actions{
  display: flex;
  justify-content: center;
}
q-dialog {
  display: flex;
  justify-content: center;
}
.my-card:hover {
  background: rgba(32, 28, 28, 0.742);
  transform: scale(1.05);
}
.card-image {
  width: 200px;
  transition: transform 0.3s ease;
  
  &:hover{
  transform: scale(1.1) rotate(3deg);
  }
}

.modal-image {
  width: 100%;
  max-width: 250px;
  border-radius: 10px;
}
.model-card{
  color: $white;
  background-color: $dark-green;

}
.q-btn {
  cursor: pointer;
  background-color:#d9c251;
   border-radius: 2rem;
  color: #181d06!important;
  width: 200px;
  font-family: var(--font-montserrat-bold);
  font-weight: var(--font-weight-bold);
}
.q-btn:hover {
  background-color:  $green-hover;
  transform: scale(1.05); 
}
.btn-alert {
  color: $black;
}
@media (max-width: 768px) {
  .col-md-4 {
    width: 100%
  }
}
</style>
