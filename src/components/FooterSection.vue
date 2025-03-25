<template>
  <q-layout>
    <!-- Footer -->
    <q-footer elevated class="bg-dark-green text-white q-pa-md">
      <div class="footer-container row justify-between items-center">
        <!-- Left: Logo & Quick Links -->
        <div class="col-12 col-md-4 text-center text-md-left">
          <div class="footer-links">
            <q-btn flat to="/" label="Home" class="text-white" />
            <q-btn flat to="/menu" label="Menu" class="text-white" />
            <q-btn flat to="/plan" label="Plan" class="text-white" />
            <q-btn flat to="/snacks" label="Snacks" class="text-white" />
            <q-btn flat to="/gear" label="Gear" class="text-white" />
            <q-btn flat to="/fire" label="Fire & Safety" class="text-white" />
            <q-btn flat to="/wildlife" label="Wildlife" class="text-white" />
          </div>
        </div>

        <!-- Center: Social Media Links -->
        <div class="col-12 col-md-4 text-center">
          <q-btn
            round
            flat
            icon="fa-brands fa-facebook"
            class="text-white"
            href="https://facebook.com"
            target="_blank"
          />
          <q-btn
            round
            flat
            icon="fa-brands fa-twitter"
            class="text-white"
            href="https://twitter.com"
            target="_blank"
          />
          <q-btn
            round
            flat
            icon="fa-brands fa-instagram"
            class="text-white"
            href="https://instagram.com"
            target="_blank"
          />
          <q-btn
            round
            flat
            icon="fa-brands fa-youtube"
            class="text-white"
            href="https://youtube.com"
            target="_blank"
          />
        </div>

        <!-- Right: Copyright Info -->
        <div class="col-12 col-md-4 text-center text-md-right">
          <p class="q-mb-none">
            © {{ new Date().getFullYear() }} Camping Guide. All rights reserved.
          </p>
          <p class="q-mb-none">
            <q-btn
              flat
              to="/privacy"
              label="Privacy Policy"
              class="text-white text-caption"
            />
            <q-btn
              flat
              to="/terms"
              label="Terms of Use"
              class="text-white text-caption"
            />
          </p>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>
<style scoped>
.bg-dark-green {
  background-color: #1c3b24; /* Deep Army Green */
}
.q-layout {
  min-height: 0px !important;
}
.footer-container {
  z-index: 10; /* Make sure it's above other elements */
  width: 100%;
  background-color: #1c3b24; /* Dark army green for contrast */
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
