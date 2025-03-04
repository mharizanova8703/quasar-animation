<template>
  <div class="find-campsite-section q-pa-lg">
    <h2 class="text-center text-bold text-amber-7">🏕️ Find Your Perfect Campsite</h2>
    <p class="text-center q-mt-md">Explore the best camping spots near you!</p>

    <div id="map-container">
      <div id="map"></div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref, nextTick } from "vue";
import L from "leaflet";

const mapInstance = ref(null);

onMounted(() => {
  nextTick(() => {
    // Ensure map is only initialized once
    if (!mapInstance.value) {
      mapInstance.value = L.map("map", {
        center: [37.7749, -122.4194], // Default to SF
        zoom: 10,
        scrollWheelZoom: false,
      });

      L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
        attribution: "© OpenStreetMap contributors",
      }).addTo(mapInstance.value);

      // Auto-locate user's position
      if (navigator.geolocation) {
        navigator.geolocation.getCurrentPosition(
          (position) => {
            const userLocation = [position.coords.latitude, position.coords.longitude];
            mapInstance.value.setView(userLocation, 12);

            L.marker(userLocation)
              .addTo(mapInstance.value)
              .bindPopup("You are here!")
              .openPopup();

            setTimeout(() => {
              mapInstance.value.invalidateSize(); // Fix rendering issues
            }, 500);
          },
          () => {
            console.warn("Geolocation permission denied.");
          }
        );
      }

      // Ensure correct size after rendering
      setTimeout(() => {
        mapInstance.value.invalidateSize();
      }, 500);
    }
  });
});
</script>

<style scoped>
.find-campsite-section {
  text-align: center;
  background-color: #1c3b24; /* Army green */
  color: white;
  padding: 20px;
  border-radius: 12px;
}

#map-container {
  width: 100%;
  max-width: 900px;
  height: 500px;
  margin: auto;
  margin-top: 20px;
  border-radius: 8px;
  overflow: hidden;
  background: #ccc; /* Placeholder before map loads */
}

#map {
  width: 100%;
  height: 100%;
  border-radius: 8px;
}
</style>
