<template>
  <div class="">
    <NavbarHeader />
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
      <CardSection />
      <div class="text-center">
        <!-- <h1 class="text-center">
          You're Ready to Explore Stay Safe & Have Fun!
        </h1> -->
      </div>
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
    <div class="camper-van-container">
      <img ref="camperVan" class="camper-van" src="camper-van.png" />
    </div>
  </div>
  <div>
    <FooterSection />
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";
import MainHeader from "src/components/MainHeader.vue";
import WelcomeGuide from "src/components/WelcomeGuide.vue";
import CardSection from "src/components/CardSection.vue";
import NavbarHeader from "src/components/NavbarHeader.vue";
import FooterSection from "src/components/FooterSection.vue";
const camperVan = ref(null);

const handleScroll = () => {
  const scrollHeight =
    document.documentElement.scrollHeight - window.innerHeight;
  const scrollPosition = window.scrollY;

  if (scrollPosition >= scrollHeight - 100) {
    camperVan.value.style.transform = "translateX(100vw)";
    camperVan.value.style.transition =
      "transform 4s linear, opacity 2s ease-in 2s";
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
.waviy {
  position: relative;
}
.waviy span {
  position: relative;
  display: inline-block;
  font-size: 40px;
  color: #fff;
  text-transform: uppercase;
  animation: flip 2s infinite;
  animation-delay: calc(0.2s * var(--i));
}
@keyframes flip {
  0%,
  80% {
    transform: rotateY(360deg);
  }
}
.q-parallax {
  position: static;
  z-index: 0;
  height: 100%;
}

.q-parallax__media > img {
  bottom: auto;
}
h1 {
  font-size: 3rem;
  margin: auto;
  font-weight: 700;
  font-family: "Montserrat", serif;
  text-align: center;
  background: linear-gradient(90deg, #ffa500, #ffd700, #ff8c00);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  animation: gradientMove 4s infinite alternate ease-in-out;
}

/* Subtle movement effect */
@keyframes gradientMove {
  0% {
    background-position: 0% 50%;
  }
  100% {
    background-position: 100% 50%;
  }
}

/* Optional: Glowing Effect for More Visibility */
h1::after {
  content: attr(data-text);
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  color: rgba(255, 140, 0, 0.7); /* Soft orange glow */
  z-index: -1;
  text-shadow: 2px 2px 10px rgba(255, 140, 0, 0.5);
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
p {
  position: relative;
  font-family: sans-serif;
  text-transform: uppercase;
  margin: auto;
  font-size: 2em;
  letter-spacing: 4px;
  overflow: hidden;
  background: linear-gradient(90deg, #000, #fff, #000);
  background-repeat: no-repeat;
  background-size: 80%;
  animation: animate 3s linear infinite;
  -webkit-background-clip: text;
  -webkit-text-fill-color: rgba(255, 255, 255, 0);
}

@keyframes animate {
  0% {
    background-position: -500%;
  }
  100% {
    background-position: 500%;
  }
}
@media (max-width: 768px) {
  .camper-van {
    width: 250px;
  }
}
</style>
