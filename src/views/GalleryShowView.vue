<template>
  <Section>
    <CardText
      class="bg-base-200"
      :card-title="'Galleria ' + year"
      button-text="Torna alla galleria"
      button-link="/gallery"
    >
      <p class="py-6">
        La galleria è un viaggio attraverso le immagini e i temi che hanno caratterizzato il nostro
        percorso di crescita e di riflessione. Anno: {{ year }}
      </p>
    </CardText>
    <Section>
      <div v-if="loading" class="flex justify-center items-center my-6">
        <span class="loading loading-spinner loading-lg text-accent"></span>
      </div>

      <div v-else-if="error" class="alert alert-error">
        {{ error }}
      </div>

      <div v-else class="parent">
        <div
          v-for="(image, index) in images"
          :key="index"
          class="image-card"
          :class="divCalculator(index)"
        >
          <img
            :src="image"
            :alt="`Foto ${index + 1}`"
            class="w-full h-64 object-cover rounded-4xl shadow-md hover:shadow-xl transition-shadow duration-300"
            @click="openImage(image)"
          />
        </div>
      </div>

      <!-- Modal per visualizzare l'immagine ingrandita -->
      <div
        v-if="selectedImage"
        class="fixed inset-0 bg-black bg-opacity-80 flex items-center justify-center z-50"
        @click="selectedImage = null"
      >
        <div class="max-w-4xl max-h-[90vh]">
          <img :src="selectedImage" class="max-w-full max-h-[90vh] object-contain" />
          <button
            class="absolute top-4 right-4 text-white text-3xl"
            @click.stop="selectedImage = null"
          >
            &times;
          </button>
        </div>
      </div>
    </Section>
  </Section>
</template>

<script>
import Section from '@/components/Section.vue'
import CardText from '@/components/CardText.vue'

export default {
  name: 'GalleryShowView',
  components: {
    Section,
    CardText,
  },
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
    divCalculator(index) {
      const gridColumn = index % 3

      return `div${gridColumn}`
    },

    openImage(image) {
      this.selectedImage = image
    },
  },
}
</script>

<style scoped>
.parent {
  display: grid;
  gap: 8px;
}

.div0 {
  grid-row: span 2 / span 2;
}

.div1 {
  grid-row: span 2 / span 2;
  grid-column-start: 2;
  grid-row-start: 2;
}

.div2 {
  grid-row: span 2 / span 2;
  grid-column-start: 3;
  grid-row-start: 1;
}
</style>
