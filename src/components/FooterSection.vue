<template>
  <q-layout>
    <!-- Footer -->
    <q-footer elevated class="bg-dark-green q-pa-lg">
      <div class="footer-container row q-pa-lg justify-between items-center">

        <!-- Right: Copyright Info -->
        <div class="col-12 col-md-4 text-center text-md-right">
          
          <p class="q-mb-none font-smd ">
            © {{ new Date().getFullYear() }} Camping Guide. Connect with me.
          </p>
          <p class="q-mb-none q-pt-md">
        <a
          href="https://www.linkedin.com/in/mariya-harizanova-a9651b219/"
          class="icon-link"
          target="_blank" 
          rel="noopener noreferrer"
        >
          <img class="soc-icon" src="linkedin.png" alt="linkedin" />
        </a>
        <a
          href="https://x.com/MariyaHari81424"
          target="_blank"
        >
          <img class="soc-icon" src="twitter.png" alt="twitter"/>
        </a>
      </p>
        </div>
      </div>
    </q-footer>
  </q-layout>
</template>
<style scoped lang="scss">
.bg-dark-green {
  background-color: $dark-green;
}
.q-layout {
  min-height: 0px !important;
}
.footer-container {
  z-index: 10;
  width: 100%;
  background-color: $dark-green;
  display: flex;
  flex-direction: column;
  justify-content: center;
  text-align: center;
}

.q-footer {
  position: relative;
  bottom: 0;
  width: 100%;
  color: #d9c251;
}
p{
  color: $primary-yellow;
}
.soc-icon{
  width: 30px;
}
a {
  background-color: $dark-green;
  text-decoration: none;
}
.q-parallax-container {
  position: relative;
  z-index: 0;
}

.q-parallax {
  position: relative !important;
  z-index: 1 !important;
}
</style>
