<template>
  <q-layout>
    <!-- Footer -->
    <q-footer elevated class="bg-dark-green text-white q-pa-lg">
      <div class="footer-container row justify-between items-center">

        <!-- Right: Copyright Info -->
        <div class="col-12 col-md-4 text-center text-md-right">
          
          <p class="q-mb-none">
            © {{ new Date().getFullYear() }} Camping Guide. Connect with me.
          </p>
          <p class="q-mb-none">
        <a
          href="https://www.linkedin.com/in/mariya-harizanova-a9651b219/"
          target="_blank"
          class="text-white text-caption q-mr-md"
        >
          LinkedIn
        </a>
        <a
          href="https://x.com/MariyaHari81424"
          target="_blank"
          class="text-white text-caption"
        >
          Twitter
        </a>
      </p>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>
<style scoped>
.bg-dark-green {
  background-color: #031b12; /* Deep Army Green */
}
.q-layout {
  min-height: 0px !important;
}
.footer-container {
  z-index: 10; /* Make sure it's above other elements */
  width: 100%;
  background-color: #031b12; /* Dark army green for contrast */
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

/* Ensure Footer Always Stays at Bottom */
.q-footer {
  position: relative;
  bottom: 0;
  width: 100%;
  color: #d9c251;
}
p{
  color: #ffc932;
}
/* Make Sure Parallax Doesn't Hide Footer */
.q-parallax-container {
  position: relative;
  z-index: 0;
}

.q-parallax {
  position: relative !important;
  z-index: 1 !important;
}
</style>
