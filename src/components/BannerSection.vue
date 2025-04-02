<template>
  <div class="list-items">
    <div class="row q-gutter-md justify-center">
      <div class="col-sm-12 col-md-12 col-lg-12 flex justify-center">
        <q-card ref="card" class="my-card">
          <q-card-section class="text-center">
          
              <h1 class="flicker montserrat-bold">
              Escape Into Nature<br />
              Your Ultimate Camping Guide
            </h1>
              <h1 ref="heading" class="font-xxlm ">
            Where Wi-Fi is weak, memories are strong.
            </h1>
            <hr />
            <p ref="text" class="font-smd custom-copy q-mt-md q-pt-md q-mb-lg">
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

const loadGSAP = () => {
  return new Promise((resolve) => {
    if (window.gsap) return resolve(); // Prevents multiple loads
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
    scale: 0.8,
    y: 100, 
    duration: 1.2,
    ease: "back.out(1.7)"
  });

  // ✅ Heading slides in naturally
  gsap.from(heading.value, {
    opacity: 0,
    y: 30, // Less floating, more "walking in"
    duration: 1,
    delay: 0.2,
    ease: "power4.out"
  });

  // ✅ Text staggered fade-in with a solid start
  gsap.from(text.value, {
    opacity: 0,
    y: 20, // Small movement for a grounded feel
    duration: 1,
    delay: 0.4,
    ease: "power3.out"
  });
});
</script>

<style scoped lang="scss">

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
  color: $white;
  box-shadow: $box-shadow;
  background: $background;
  backdrop-filter: $backdrop-filter; 
}
.flicker {
  animation: flickerAnimation 2s infinite;
  color: $primary-yellow
}

@keyframes flickerAnimation {
  0%, 100% { opacity: 1; }
  45% { opacity: 0.9; }
  50% { opacity: 0.6; }
  55% { opacity: 0.95; }
  60% { opacity: 0.8; }
}
hr {
  width: 50%;
}
.main-copy {
  color: $primary-yellow;
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
  .custom-copy{
    width: 85%;
  }
  .flicker {
 font-size: 3rem;
 line-height: 4rem;
}
}
</style>
