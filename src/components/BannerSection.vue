<template>
  <div class="list-items">
    <div class="row q-gutter-md justify-center">
      <div class="col-sm-12 col-md-12 col-lg-12 flex justify-center">
        <q-card ref="card" class="my-card">
          <q-card-section class="text-center">
            <h1 ref="heading" class="text-bold main-copy font-xxld">
              Escape Into Nature<br />
              Your Ultimate Camping Guide
            </h1>
            <hr />
            <p ref="text" class="font-smd custom-copy q-mt-md">
              Step away from the everyday and reconnect with the wild. Breathe in the
              fresh air, feel the ground beneath your feet, and let nature do the rest.
              Roast some marshmallows by the fire, take a quiet moment to meditate, or go
              all in with a ziplining adventure. Whether you're chasing adrenaline or just
              looking to unwind, the outdoors has something for everyone. So, pack up,
              head out, and make some real memories under the open sky.
            </p>
          </q-card-section>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

// ✅ Import GSAP
const loadGSAP = () => {
  return new Promise((resolve) => {
    if (window.gsap) return resolve();
    const script = document.createElement("script");
    script.src = "https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js";
    script.onload = resolve;
    document.head.appendChild(script);
  });
};

// Refs for animation
const card = ref(null);
const heading = ref(null);
const text = ref(null);

onMounted(async () => {
  await loadGSAP();

  gsap.from(card.value, {
    opacity: 0,
    scale: 0.9,
    duration: 1.5,
    ease: "power2.out"
  });

  gsap.from(heading.value, {
    opacity: 0,
    y: 50,
    duration: 1.5,
    delay: 0.3,
    ease: "power2.out"
  });

  gsap.from(text.value, {
    opacity: 0,
    y: 30,
    duration: 1.2,
    delay: 0.5,
    ease: "power2.out"
  });
});
</script>

<style scoped>
.list-items {
  width: 100%;
  padding: 5rem 0rem;
}
.my-card {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 1rem;
  min-height: 100%;
  border-radius: 0px;
  width: 100%;
  color: white;
  box-shadow: 0 1px 5px rgb(0 0 0 / 94%), 0 2px 2px rgba(0, 0, 0, 0.14),
    0 3px 1px -2px rgba(0, 0, 0, 0.12);
  background: rgba(231, 207, 207, 0.112);
  backdrop-filter: blur(10px);
}
hr {
  width: 50%;
}
.main-copy {
  color: #f0c906;
}
.my-card:hover {
  background: rgba(231, 207, 207, 0);
  transform: scale(1.05);
}
.custom-copy {
  width: 65%;
  margin: auto;
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
