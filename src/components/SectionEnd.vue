<template>
  <div class="list-items" ref="section">
    <div class="row q-gutter-md justify-center">
      <div class="col-sm-12 col-md-12 col-lg-12 flex justify-center column items-center">
        <h1 ref="heading" class="font-xxld  montserrat-bold">
        Bold heart, packed bag — let’s blaze a new trail today.
        </h1>
        <div class="stars montserrat-bold">
          <img class="star-asset" src="star.png" />
          <img class="star-asset" src="star.png" />
          <img class="star-asset" src="star.png" />
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>
import { ref, onMounted } from "vue";

const heading = ref(null);
const section = ref(null);

onMounted(async () => {
  // Load GSAP
  if (!window.gsap) {
    await new Promise((resolve) => {
      const script = document.createElement("script");
      script.src = "https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/gsap.min.js";
      script.onload = resolve;
      document.head.appendChild(script);
    });
  }

  // Load ScrollTrigger plugin
  if (!window.ScrollTrigger) {
    await new Promise((resolve) => {
      const script = document.createElement("script");
      script.src = "https://cdnjs.cloudflare.com/ajax/libs/gsap/3.12.2/ScrollTrigger.min.js";
      script.onload = resolve;
      document.head.appendChild(script);
    });
  }

  // Register ScrollTrigger
  const gsap = window.gsap;
  gsap.registerPlugin(window.ScrollTrigger);

  // Animate heading
  gsap.from(heading.value, {
    scrollTrigger: {
      trigger: section.value,
      start: "top 80%",
      toggleActions: "play none none none"
    },
    opacity: 0,
    y: 50,
    rotationX: 90,
    ease: "elastic.out(1, 0.4)",
    duration: 1.5
  });

  // Animate stars with staggered rotation
  const stars = gsap.utils.toArray(".star-asset");

  gsap.from(stars, {
    scrollTrigger: {
      trigger: section.value,
      start: "top 80%",
      toggleActions: "play none none none"
    },
    opacity: 0,
    scale: 0.5,
    rotation: 360,
    duration: 1,
    stagger: 0.3,
    ease: "back.out(1.7)"
  });
});
</script>
<style scoped lang="scss">
.list-items {
  padding: 5rem 0;
  text-align: center;
}

h1 {
  color: $primary-yellow;
  max-width: 700px;
  margin: 0 auto 1rem;
}

.stars {
  display: flex;
  justify-content: center;
  gap: 1rem;
  margin-top: 1.5rem;
}

.star-asset {
  width: 35px;
  height: 35px;
  transform-origin: center center;
}
</style>
