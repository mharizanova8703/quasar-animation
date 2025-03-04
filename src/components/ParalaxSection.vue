<template>
  <div class="parallax-container">
    <!-- Parallax Background -->
    <div class="q-parallax">
      <div class="q-parallax__media">
        <img ref="mountain" class="mountain" src="bg-forest.png" />
      </div>
    </div>

    <!-- Camper Van -->
    <div class="camper-van-container">
      <img ref="camperVan" class="camper-van" src="camper-van.png" />
    </div>
  </div>
</template>

<script setup>
import { onMounted, onUnmounted, ref } from "vue";

const camperVan = ref(null);

const handleScroll = () => {
  const scrollHeight = document.documentElement.scrollHeight - window.innerHeight;
  const scrollPosition = window.scrollY;
  const maxMove = window.innerWidth * 0.7; // Maximum movement distance

  if (scrollPosition >= scrollHeight - 100) {
    // When reaching the bottom, move off-screen & fade out
    camperVan.value.style.transform = `translateX(${maxMove}px)`;
    camperVan.value.style.transition = "transform 4s linear, opacity 2s ease-in 2s";
    setTimeout(() => {
      camperVan.value.style.opacity = "0";
    }, 4000);
  } else {
    // Reset when scrolling up
    camperVan.value.style.transform = "translateX(0)";
    camperVan.value.style.opacity = "1";
    camperVan.value.style.transition = "transform 1s ease-out, opacity 0.5s ease-in";
  }
};

onMounted(() => {
  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
/* Main Container */
.parallax-container {
  position: relative;
  overflow: hidden;
  height: 100vh;
  display: flex;
  align-items: flex-end;
}

/* Parallax Background (Forest) */
.q-parallax {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100vh;
  z-index: -1;
}

.q-parallax__media {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
}

.q-parallax__media img {
  width: 100%;
  height: auto;
  max-height: 100vh;
  object-fit: cover;
  transition: transform 0.3s ease-out;
}

/* Camper Van */
.camper-van-container {
  position: absolute;
  bottom: 0;
  left: 10%;
  z-index: 10;
}

.camper-van {
  width: 300px;
  transition: transform 0.5s ease-in-out;
  transform: scaleX(-1); /* Flips the van to face the right */
}
</style>
