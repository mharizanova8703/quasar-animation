<template>
  <div class="q-pa-md q-mx">
    <div class="q-gutter-md row">
      <div class="col-12 col-lg-7 q-mx-auto">
        <q-carousel
          animated
          v-model="slide"
          arrows
          navigation
          infinite
          height="400px"
        >
          <q-carousel-slide
            v-for="(img, index) in campingImages"
            :key="index"
            :name="index"
            :img-src="img"
          />
        </q-carousel>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const slide = ref(0)
const campingImages = ref([])
const ACCESS_KEY = import.meta.env.VITE_UNSPLASH_KEY

onMounted(async () => {
  try {
    const res = await axios.get('https://api.unsplash.com/search/photos', {
      params: {
        query: 'camping',
        per_page: 6,
      },
      headers: {
        Authorization: `Client-ID ${ACCESS_KEY}`
      }
    })

    campingImages.value = res.data.results.map(img => img.urls.regular)
  } catch (err) {
    console.error('Error fetching camping images:', err)
  }
})
</script>
