<template>
  <div class="list-items">
    <div class="row q-gutter-md justify-center">
      <div
        v-for="(card, index) in cards"
        :key="index"
        class="col-12 col-sm-6 col-md-4 col-lg-3 flex justify-center"
      >
        <q-card class="my-card">
          <q-card-section>
           <q-img :src="card.img" class="card-image" />
            <div class="text-h6 text-center">{{ card.title }}</div>
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
    title: "Menu Plan",
    text: "Plan a menu that is easy to cook and nutritious.",
    img: "food.png"
  },
  {
    title: "Snacks",
    text: "Bring snacks like nuts, dried fruit, and granola.",
    img: "snack.png"
  },
  {
    title: "Drinking Water",
    text: "Make sure you bring enough drinking water or a water filter.",
    img: "water.png"
  }
]);

</script>

<style scoped>
.list-items {
  width: 100%;
  padding: 3rem 0rem;
}
.my-card {
  padding: 15px;
  border-radius: 10px;
  width: 100%;
  color: white;
  background: rgba(231, 207, 207, 0.112);
  backdrop-filter: blur(10px); 
}
.my-card:hover {
  background: rgba(231, 207, 207, 0.3);
  transform: scale(1.05);
}
.card-image{
  width:200px;
}
@media (max-width: 768px) {
  .col-md-4 {
    width: 100%;
  }
}
</style>
