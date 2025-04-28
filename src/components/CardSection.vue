<template>
  <div>
    <div class="list-items">
      <div class="row q-gutter-md justify-center">
        <div
          v-for="(card, index) in cards"
          :key="index"
          class="col-11 col-sm-6 col-md-3 col-lg-3 flex justify-center"
        >
          <q-card class="my-card q-mb-lg">
            <q-card-section class="text-center">
              <q-img ref="images" :src="card.img" class="card-image" />
              <div class="font-pxl text-center montserrat-bold">{{ card.title }}</div>
              <div class="text-subtitle2 text-center">{{ card.author }}</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
              {{ card.text.length > 50 ? card.text.substring(0, 50) + "..." : card.text }}
            </q-card-section>

            <q-btn label="Read More" color="yellow-orange  btn-alert" @click="openModal(card)" />
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
          <q-btn flat label="Close" color="yellow-orange q-my-auto q-mb-lg" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
  
</template>

<script setup>
import { ref, onMounted } from "vue";

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
const modalImage = ref(null);

const cards = ref([
  {
    title: "Shoes",
    text:
      "Choosing the right footwear is essential. Hiking boots provide ankle support, waterproof shoes protect against wet trails, and sandals are perfect for casual campsite wear. Make sure your shoes are broken in before the trip!",
    img: "boots.png",
    alert: false,
  },
  {
    title: "Camping Fire",
    text:
      "Fire is essential for warmth, cooking, and safety. Bring waterproof matches, fire starters, and dry kindling. Follow Leave No Trace principles—only build fires in designated areas and extinguish them completely before leaving.",
    img: "wild-fire.png",
    alert: false,
  },
  {
    title: "Wild Animals",
    text:
      "Wildlife encounters are part of camping. Store food in bear-proof containers, never feed animals, and know how to react to encounters with bears, snakes, or coyotes. Keep your distance and respect their habitat.",
    img: "wild-life.png",
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
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 1rem;
  min-height: 100%;
  border-radius: 10px;
  width: 100%;
  color: white;
  box-shadow: $box-shadow;
  background: $background;
  backdrop-filter: $backdrop-filter;
}
.q-dialog__backdrop {
    z-index: -1;
    pointer-events: all;
    outline: 0;
    background: rgb(4, 3, 3);
}
.q-card__actions{
  display: flex;
  justify-content: center;
}
.model-card{
  color: white;
  background-color: $dark-green;

}
q-dialog {
  display: flex;
  justify-content: center;
}
.my-card:hover {
  background: rgba(231, 207, 207, 0);
  transform: scale(1.05);
}
.card-image {
  width: 200px;
  transition: transform 0.3s ease;
}
.card-image:hover {
  transform: scale(1.1) rotate(3deg);
}

.modal-image {
  width: 100%;
  max-width: 250px;
  border-radius: 10px;
}
.q-btn {
  cursor: pointer;
  background-color: #d9c251;
   border-radius: 2rem;
  color: #181d06!important;
  width: 200px;
  font-family: var(--font-montserrat-bold);
  font-weight: var(--font-weight-bold);
}
.q-btn:hover {
  background-color: #387566;
  transform: scale(1.05); 
}
.btn-alert {
  color: black;
}
@media (max-width: 768px) {
  .col-md-4 {
    width: 100%
  }
}
</style>
