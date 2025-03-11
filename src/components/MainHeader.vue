<template>
  <div class="list-items">
    <div class="row q-gutter-md justify-center">
      <div
        v-for="(card, index) in cards"
        :key="index"
        class="col-12 col-sm-6 col-md-3 col-lg-3 flex justify-center"
      >
        <q-card class="my-card">
          <q-card-section>
            <q-img :src="card.img" class="card-image" />
            <div class="font-pxl text-center montserrat-bold">
              {{ card.title }}
            </div>
            <div class="text-subtitle2 text-center">{{ card.author }}</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            {{ card.text }}
          </q-card-section>
          <q-btn label="Alert" color="yellow-orange q-mb-md btn-alert" @click="card.alert = true" />
        </q-card>
        <q-dialog v-model="card.alert">
          <q-card>
            <q-card-section>
              <div class="text-h6 alert-btn mx-auto">Alert</div>
            </q-card-section>

            <q-card-section class="q-pt-none">
              Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum repellendus
              sit voluptate voluptas eveniet porro. Rerum blanditiis perferendis totam, ea
              at omnis vel numquam exercitationem aut, natus minima, porro labore.
            </q-card-section>

            <q-card-actions align="right">
              <q-btn flat label="OK" color="yellow-orange q-my-auto" v-close-popup />
            </q-card-actions>
          </q-card>
        </q-dialog>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

onMounted(() => {
  const script = document.createElement("script");
  script.src =
    "https://unpkg.com/@dotlottie/player-component@2.7.12/dist/dotlottie-player.mjs";
  script.type = "module";
  document.head.appendChild(script);
});

const cards = ref([
  {
    title: "Menu Plan",
    text:
      "A well-planned camping menu keeps you energized for outdoor activities. Pack easy-to-cook meals like foil-wrapped veggies, grilled meats, pasta, and one-pot meals. Don’t forget high-energy snacks and hydration!",
    img: "food.png",
  },
  {
    title: "Snacks",
    text:
      "Quick snacks are a must for camping. Pack protein bars, nuts, dried fruits, jerky, and s’mores ingredients. Bring some easy-to-carry trail mix for energy boosts during hikes!",
    img: "snack.png",
  },
  {
    title: "Drinking Water",
    text: "Make sure you bring enough drinking water or a water filter.",
    img: "water.png",
  },
]);
</script>

<style scoped>
.card-title {
  min-height: 50px;
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
  font-size: 1.2rem;
  font-weight: bold;
}

.list-items {
  margin-top: 5rem;
  position: relative;
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
  padding: 15px;
  border-radius: 10px;
  width: 100%;
  color: white;
  background: rgba(231, 207, 207, 0.112);
  backdrop-filter: blur(10px);
  box-shadow: 0 1px 5px rgb(0 0 0 / 94%), 0 2px 2px rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12);
}
.my-card:hover {
  background: rgba(231, 207, 207, 0);
  transform: scale(1.05);
}

.card-image {
  width: 200px;
}
.q-btn {
  cursor: pointer;
  background-color: #387566;
   border-radius: 2rem;
  color: #181d06!important;
  width: 200px;
  font-family: var(--font-montserrat-bold);
  font-weight: var(--font-weight-bold);
}
.q-btn:hover {
  background-color: #d9c251;
  transform: scale(1.05); 
}
@media (max-width: 768px) {
  .col-md-4 {
    width: 100%;
  }
}
</style>
