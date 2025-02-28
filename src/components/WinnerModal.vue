<template>
  <div class="q-pa-md q-gutter-sm">
    <q-btn label="Show Winner" color="primary" @click="openModal" />

    <q-dialog v-model="dialog">
      <q-card style="width: 400px; text-align: center">
        <!-- Lottie Animation -->
        <dotlottie-player
          ref="lottie"
          id="lottie-animation"
          src="https://lottie.host/5b751db2-d5a7-4914-90d9-875c7cd78c9d/an3LmOhG2e.lottie"
          background="transparent"
          speed="1"
          style="width: 300px; height: 300px"
          loop
          autoplay
        ></dotlottie-player>

        <q-card-section>
          <div class="text-h6">🎉 Congratulations! 🎉</div>
          <div class="text-grey">You are the lucky winner! 🏆</div>
        </q-card-section>

        <q-card-actions align="center">
          <q-btn label="Awesome!" color="primary" @click="closeModal" />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </div>
</template>

<script setup>
import { ref, onMounted, nextTick } from "vue";

const dialog = ref(false);

const openModal = async () => {
  dialog.value = true;
  await nextTick(); // Wait for modal to render before playing Lottie animation

  const lottiePlayer = document.getElementById("lottie-animation");
  if (lottiePlayer) {
    lottiePlayer.play();
  }
};

const closeModal = () => {
  dialog.value = false;
};

// Load Lottie Player dynamically
onMounted(() => {
  if (!document.querySelector("script[src*='dotlottie']")) {
    const script = document.createElement("script");
    script.src = "https://unpkg.com/@dotlottie/player-component@2.7.12/dist/dotlottie-player.mjs";
    script.type = "module";
    document.body.appendChild(script);
  }
});
</script>
