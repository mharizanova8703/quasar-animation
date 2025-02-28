
 <template>
  <div class="">
      <WelcomeGuide />
    <div class="row justify-between">
      <dotlottie-player
        src="https://lottie.host/03b9aaa3-16fc-4ed3-96c8-c6fe7d1db49c/hc3dqvRXN0.lottie"
        background="transparent"
        speed="1"
        class="moon-animation"
        loop
        autoplay
      ></dotlottie-player>
       <MainHeader ref="headerComponent" />
      <CardSection/>
      <div class="q-parallax" style="height: 500px">
        <div class="q-parallax__media">
          <img
            class="mountain"
            src="bg-mountains.png"
            style="display: initial; transform: translate3d(-50%, 414px, 0px)"
          />
        </div>
        <div class="q-parallax__content absolute-full column flex-center"></div>
      </div>
    </div>

    <!-- Camper Van (Animated at Bottom) -->
    <div class="camper-van-container">
      <img ref="camperVan" class="camper-van" src="camper-van.png" />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import MainHeader from "src/components/MainHeader.vue";
import WelcomeGuide from "src/components/WelcomeGuide.vue"; 
import CardSection from "src/components/CardSection.vue"; 
const camperVan = ref(null);

const handleScroll = () => {
  const scrollHeight = document.documentElement.scrollHeight - window.innerHeight;
  const scrollPosition = window.scrollY;

  if (scrollPosition >= scrollHeight - 100) {
    // 🚐 Move camper van across the screen when user reaches bottom
    camperVan.value.style.transform = "translateX(100vw)";
    camperVan.value.style.transition = "transform 4s linear, opacity 2s ease-in 2s";

    // ⏳ Make it fade out after moving
    setTimeout(() => {
      camperVan.value.style.opacity = "0";
    }, 4000);
  } else {
    // Reset when scrolling up
    camperVan.value.style.transform = "translateX(0)";
    camperVan.value.style.opacity = "1";
  }
};

onMounted(() => {
  // Restore Moon Animation JavaScript
  const header = ref(null);
  const script = document.createElement("script");
  script.src =
    "https://unpkg.com/@dotlottie/player-component@2.7.12/dist/dotlottie-player.mjs";
  script.type = "module";
  document.head.appendChild(script);

  window.addEventListener("scroll", handleScroll);
});

onUnmounted(() => {
  window.removeEventListener("scroll", handleScroll);
});
</script>

<style scoped>
/* 🌄 Parallax Settings */
.q-parallax {
  position: static;
  z-index: 0;
  height: 100%;
}

.q-parallax__media > img {
  bottom: auto;
}
.moon-animation {
  width: 200px;
  height: 200px;
  position: fixed;
  top: 100vh;
  left: 10%;
  z-index: 10;
}

.camper-van-container {
  position: relative;
  min-height: 100vh;
}
.mountain {
  height: 100%;
}
.camper-van {
  position: absolute;
  bottom: 0;
  left: 10%;
  width: 400px;
  z-index: 10;
  transition: transform 0.5s ease-in-out, opacity 0.5s ease-in-out;
}

/* Responsive */
@media (max-width: 768px) {
  .camper-van {
    width: 250px;
  }
}
</style>
