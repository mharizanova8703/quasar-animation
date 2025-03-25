<template>
  <div class="col-12 welcome-guide text-center">
<dotlottie-player
  src="https://lottie.host/c8c18832-eb19-4a36-9ca1-1d923a9a5f90/NOO2ADBUhY.lottie"
  background="transparent"
  speed="1"
  style="width: 200px; height: 200px"
  loop
  class="lottie-moon"
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
.lottie-moon {
  position: absolute;
  top: 15%;
  left: 85%;
}
</style>
