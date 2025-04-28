<template>
  <q-layout>
 <q-footer elevated class="bg-dark-green q-pa-lg">
  <div class="footer-container row q-pa-lg justify-between items-center">

    <!-- Left or Centered Message -->
    <div class="col-12 text-center q-mb-md">
      <p class="q-mb-xs font-smd">
        Made with ❤️ for all camping lovers out there. Let's keep exploring new trails together!
      </p>
      <p class="q-mb-md font-smd">
        Connect with me — I love hearing your camping stories!
      </p>
    </div>

    <!-- Right: Copyright Info + Social Links -->
    <div class="col-12 text-center">
      <p class="q-mb-none font-smd">
        © {{ new Date().getFullYear() }} Camping Guide. All rights reserved.
      </p>
      <div class="q-mt-md">
        <a
          href="https://www.linkedin.com/in/mariya-harizanova-a9651b219/"
          class="icon-link q-mr-md"
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
      </div>
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
.soc-icon {
  width: 30px;
  transition: transform 0.3s ease;
}

.soc-icon:hover {
  transform: scale(1.2);
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
