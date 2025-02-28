<template>
  <div class="col-12 welcome-guide text-center">
    <img class="sign-copy" src="sign-guide.png" />
    <dotlottie-player
      src="https://lottie.host/f0d8c0ad-33f2-430f-b9eb-4e1ecb02c94a/IP3bVp9Ta1.lottie"
      background="transparent"
      class="lottie-sun"
      speed="1"
      style="width: 300px; height: 300px"
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
.welcome-guide {
  background-image: url("sky-blue.jpg");
  background-size: 100% 100%;
  min-height: 60vh;
  background-repeat: no-repeat;
}
.sign-copy {
  width: 50%;
   animation: zoomEffect 3s ease-in-out infinite alternate; /* 🔥 Animation added */
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
.lottie-sun{
    position: absolute;
    top: 10%;
}
</style>
