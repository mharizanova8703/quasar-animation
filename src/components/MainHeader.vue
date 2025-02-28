<template>
  <div class=" col-12 camping-section text-center">
    <h1 class="fade-in text-center">Things You Should Know Before Going Camping</h1>

    <div class="cards-container">
      <div
        v-for="(text, index) in fadeOutTexts"
        :key="'text-' + index"
        class="fade-out-text"
        :class="{ fadeOut: activeCard > index }"
        :style="{ top: `${index * 100}vh` }"
      >
        <h2>{{ text }}</h2>
      </div>

      <!-- 🏕️ Camping Cards -->
      <div
        v-for="(card, index) in cards"
        :key="'card-' + index"
        class="camp-card"
        :class="{
          slideInLeft: index % 2 === 0 && activeCard === index && hasScrolled,
          slideInRight: index % 2 !== 0 && activeCard === index && hasScrolled,
          fadeOut: activeCard !== index && hasScrolled
        }"
        :style="{ top: `${index * 100}vh` }"
      >
        <h2>{{ card.title }}</h2>
        <p>{{ card.text }}</p>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const activeCard = ref(-1);
const hasScrolled = ref(false);


const cards = [
  { title: "🔥 Fire Safety", text: "Check fire restrictions before camping and never leave a fire unattended." },
  { title: "🏕️ Choosing the Right Spot", text: "Find a dry, flat spot for your tent away from water sources." },
  { title: "🍃 Leave No Trace", text: "Pack out all trash and respect nature by following Leave No Trace principles." },
  { title: "🧳 Packing Essentials", text: "Bring warm clothes, first aid, and enough food for your adventure!" }
];

// 🔥 Scroll event to switch cards
const handleScroll = () => {
  hasScrolled.value = true; // Only trigger animations once scrolling starts
  const scrollY = window.scrollY;
  const index = Math.min(Math.floor(scrollY / window.innerHeight * 1.2), cards.length);
  activeCard.value = index;
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>
<style scoped>
/* 🌲 Camping Section */
.camping-section {
  text-align: center;
  background-repeat: no-repeat;
padding: 0;
}

h1 {
  font-size: 2.5rem;
  margin-bottom: 40px;
    text-align: center;
    background-color: rgb(255, 178, 62);
    background-image: linear-gradient(268.67deg, rgb(255, 255, 255) 3.43%, rgb(255, 240, 102) 15.69%, rgb(255, 163, 26) 55.54%, rgb(255, 0, 115) 99%);
    background-size: 100%;
    background-clip: text;
    -webkit-text-fill-color: transparent;
}
.cards-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 200vh; /* Reduces space between cards */
  position: relative;
}

/* 📢 Fade-Out Text Before Each Card */
.fade-out-text {
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  font-size: 1.8rem;
  font-weight: bold;
  color: #444;
  transition: opacity 0.8s ease-in-out;
  opacity: 1;
}

/* 📜 Camping Tip Cards */
.camp-card {
  background: white;
  width: 50%;
  max-width: 500px;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.1);
  position: absolute;
  text-align: left;
  transition: all 0.8s ease-in-out;
  opacity: 0;
  z-index: 10;
}

/* 🌟 Slide in from left */
.slideInLeft {
  opacity: 1;
  left: 10%;
  transform: translateX(0);
}

/* 🌟 Slide in from right */
.slideInRight {
  opacity: 1;
  right: 10%;
  transform: translateX(0);
}

/* 📉 Fade out effect */
.fadeOut {
  opacity: 0;
  transition: opacity 0.8s ease-in-out;
}
</style>
