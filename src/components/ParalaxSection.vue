<template>
  <div class="parallax-container">
    <!-- Parallax Background -->
    <div class="q-parallax">
      <div class="q-parallax__media">
        <!-- Remove the img tag for the mountain -->
        <!-- <img ref="mountain" class="mountain" src="bg-forest.png" /> -->
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
.parallax-container {
  position: relative;
  background-image: url('forest-bg.png');
  background-size: 100%;
  background-repeat: no-repeat;
  background-size: 100%;
  background-position: center;
}

.camper-van-container {
  position: relative;
  min-height: 90vh;
}


/* .mountain {
  height: 100%;
  width: contain;
} */

.camper-van {
  position: absolute;
  bottom: 0;
  left: 10%;
  width: 400px;
  z-index: 10;
  transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;
}
</style>