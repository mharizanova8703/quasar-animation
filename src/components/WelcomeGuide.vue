<template>
  <div class="col-12 welcome-guide text-center">
    <!-- <img class="sign-copy" src="sign-guide.png" /> -->
    <!-- <dotlottie-player
      src="https://lottie.host/f0d8c0ad-33f2-430f-b9eb-4e1ecb02c94a/IP3bVp9Ta1.lottie"
      background="transparent"
      class="lottie-sun"
      speed="1"
      style="width: 300px; height: 300px"
      loop
      autoplay
    ></dotlottie-player> -->
    <dotlottie-player
      src="https://lottie.host/03b9aaa3-16fc-4ed3-96c8-c6fe7d1db49c/hc3dqvRXN0.lottie"
      background="transparent"
      speed="1"
      class="lottie-sun"
      style="width: 200px; height: 200px"
      loop
      autoplay
    ></dotlottie-player>
  </div>
</template>

<script setup>
import { onMounted } from "vue";

onMounted(() => {
  const script = document.createElement("script");
  script.src =
    "https://unpkg.com/@dotlottie/player-component@2.7.12/dist/dotlottie-player.mjs";
  script.type = "module";
  document.head.appendChild(script);
});
</script>

<style scoped>
.sign-copy {
  width: 50%;
  animation: zoomEffect 3s ease-in-out infinite alternate;
}
@keyframes zoomEffect {
  0% {
    transform: scale(1);
    opacity: 0.6;
  }
  100% {
    transform: scale(1.1);
    opacity: 1;
  }
}
.lottie-sun {
  position: absolute;
  top: 10%;
}
</style>
