<template>
  <div class="carousel w-full max-h-48">
    <div
      v-for="(image, index) of images"
      :id="`slide${index}`"
      class="carousel-item relative w-full"
    >
      <img :src="image" class="w-full object-cover" />
      <div class="absolute left-5 right-5 top-1/2 flex -translate-y-1/2 transform justify-between">
        <a :href="`#slide${index - 1}`" class="btn btn-accent">❮</a>
        <a :href="`#slide${index + 1}`" class="btn btn-accent">❯</a>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'GalleryShowView',
  props: {
    year: {
      type: String,
      required: true,
    },
  },

  data() {
    return {
      images: [],
      loading: true,
      error: null,
      selectedImage: null,
    }
  },

  created() {
    this.fetchImages()
  },

  methods: {
    fetchImages() {
      try {
        this.loading = true

        // In un'applicazione reale useremmo un'API per ottenere l'elenco dei file,
        // ma poiché stiamo lavorando con file statici in public, dobbiamo conoscere i nomi in anticipo

        // Otteniamo tutti i file dalla cartella uomomondo-2023-24
        const imageBasePath = '/images/uomomondo-2023-24/'

        // Lista dei file che sappiamo essere presenti nella cartella
        const imageFiles = [
          'FB_IMG_1708379356308.jpg',
          'IMG20231215121402.jpg',
          'IMG20231215123955.jpg',
          'IMG20231221153137.jpg',
          'IMG20231221154015.jpg',
          'IMG20231221155538.jpg',
          'IMG20231221155823.jpg',
          'IMG20231221155834.jpg',
          'IMG20231221163217.jpg',
          'IMG20231221163801.jpg',
          'IMG20231221164718.jpg',
          'IMG20231221164732.jpg',
          'IMG20231221165407.jpg',
          'IMG20231221170757.jpg',
          'IMG20231221172831.jpg',
          'IMG20231221175115.jpg',
          'IMG20231221175128.jpg',
          'IMG20240131160647.jpg',
          'IMG20240131160726.jpg',
          'IMG20240131161325.jpg',
          'IMG20240216084341.jpg',
          'IMG20240216151917.jpg',
          'IMG20240216162030.jpg',
          'IMG20240221160247.jpg',
          'IMG20240315110133.jpg',
          'Manifesto MORO-Grassi-2.jpg',
          'VID20240221160500.jpg',
          'VID20240221162645.jpg',
          'VID20240221170315.jpg',
          'Video WhatsApp 2024-02-16 ore 14.24.02_fb3e5dfb.jpg',
        ]

        // Aggiungiamo il percorso base a ciascun nome di file
        this.images = imageFiles.map((file) => imageBasePath + file)

        this.loading = false
      } catch (err) {
        this.error = 'Errore nel caricamento delle immagini: ' + err.message
        this.loading = false
      }
    },
  },
}
</script>

<style scoped></style>
