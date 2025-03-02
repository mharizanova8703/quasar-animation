<template>
  <div class="list-items">
    <div class="row q-gutter-md justify-center">
      <div
        v-for="(card, index) in cards"
        :key="index"
        class="col-12 col-sm-6 col-md-4 col-lg-3 flex justify-center"
      >
        <q-card class="my-card">
          <q-card-section class="text-center">
            <q-img :src="card.img" class="card-image" />
            <div class="font-pxl text-center montserrat-bold">{{ card.title }}</div>
            <div class="text-subtitle2 text-center">{{ card.author }}</div>
          </q-card-section>

          <q-card-section class="q-pt-none">
            {{ card.text }}
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

onMounted(() => {
  const script = document.createElement("script");
  document.head.appendChild(script);
});

const cards = ref([
  {
    title: "Shoes",
    text: "Choosing the right footwear is essential. Hiking boots provide ankle support, waterproof shoes protect against wet trails, and sandals are perfect for casual campsite wear. Make sure your shoes are broken in before the trip!",
    img: "boots.png",
  },
  {
    title: "Camping Fire ",
    text: "Fire is essential for warmth, cooking, and safety. Bring waterproof matches, fire starters, and dry kindling. Follow Leave No Trace principles—only build fires in designated areas and extinguish them completely before leaving.",
    img: "wild-fire.png",
  },
  {
    title: "Wild Animals",
    text: "Wildlife encounters are part of camping. Store food in bear-proof containers, never feed animals, and know how to react to encounters with bears, snakes, or coyotes. Keep your distance and respect their habitat.",
    img: "wild-life.png",
  },
]);
</script>

<style scoped>
.list-items {
  width: 100%;
  padding: 3rem 0rem;
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
  box-shadow: 0 1px 5px rgb(0 0 0 / 94%), 0 2px 2px rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12);
  background: rgba(231, 207, 207, 0.112);
  backdrop-filter: blur(10px);
}
.my-card:hover {
  background: rgba(231, 207, 207, 0);
  transform: scale(1.05);
}
.card-image {
  width: 200px;
}
@media (max-width: 768px) {
  .col-md-4 {
    width: 100%;
  }
}
</style>
