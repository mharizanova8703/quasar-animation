<template>
  <div class="parallax-container">
    <!-- Parallax Background -->
    <div class="q-parallax">
      <div class="q-parallax__media">
        <img ref="mountain" class="mountain" src="bg-forest.png" />
      </div>
    </div>

    <!-- Star Background -->
    <div class="star-background">
      <img ref="star" class="star" src="star.png" />
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
  overflow: hidden;
  background-image: url('forest-bg.png'); /* Adding background image */
  background-size: 100%;
  background-position: center;
  background-repeat: no-repeat;
  
}

.q-parallax {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 1;
}

.q-parallax__media {
  width: 100%;
  height: 100%;
}

.star-background {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  z-index: 2;
  background-image: url('star.png'); /* Adding star background */
  background-size: cover;
  background-position: center;
}

.star {
  width: 100%;
  height: auto;
}

.camper-van-container {
  position: relative;
  min-height: 50vh;
  z-index: 3;
}

.mountain {
  height: 100%;
  width: contain;
}

.camper-van {
  position: absolute;
  bottom: 0;
  left: 10%;
  width: 400px;
  z-index: 10;
  transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;
}
</style>